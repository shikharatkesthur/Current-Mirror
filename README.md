# Current-Mirror

A current mirror consists of at least two transistors (usually bipolar junction transistors (BJTs) or metal-oxide-semiconductor field-effect transistors (MOSFETs)) arranged in such a way that the current flowing through one transistor (the reference transistor) is mirrored by the other transistor(s) (the output transistor(s)).
A MOSFET current mirror works similarly to a BJT current mirror. However, instead of the base-emitter voltage, the MOSFET current mirror relies on the gate-source voltage (Vgs) to establish the current. The gate-source voltage of both MOSFETs in the mirror is set equal, and by matching their dimensions and ensuring proper biasing, the output current in the mirrored transistor will be a copy of the reference current.

![image](https://github.com/user-attachments/assets/95b0a2fb-f3cc-43e4-b60c-c118430ea77d)



## Function: <br>
The primary purpose of a current mirror is to replicate a current flowing through one active device (the "input" transistor) to another active device (the "output" transistor), maintaining a constant current regardless of load conditions. In this specific configuration, the two PMOS transistors are used to create a current mirror, with the NMOS transistor acting as a current source or sink.

## Operation: <br>
The input current is set by an external source, which flows through the input PMOS transistor.<br>
The voltage drop across the input PMOS transistor is mirrored by the output PMOS transistor.<br>
This mirrored voltage drop, in turn, controls the current flow through the output PMOS transistor, creating a mirrored current.<br>

## Application <br>
**Biasing:** Current mirrors are frequently used to set bias currents in amplifier stages and other analog circuits, ensuring stable and predictable performance.<br>
**Current Sources:** They can act as precise current sources, which are useful in analog signal processing, active filters, and voltage-controlled current sources.<br>
**Active Loads:** Current mirrors are used in differential amplifier stages to provide a high output impedance, making them useful in increasing the gain of the amplifier.<br>

## Part A
## Aim: Design and Analyze Current mirror circuit as active load in amplifier circuit. 

Given :

Power Supply (VDD) = 1.8V.<br>
Power Consumption (P) <= 1mW.<br>
Gain (Av) > -10V/V.<br>

## Circuit Diagram

![image](https://github.com/user-attachments/assets/df18129a-d5f3-4d8c-bbf9-2f0aaad4bace)


## 1:1 Ratio

**For L=180nm**

**DC Analysis**

**Procedure**
1.Build the circuit as per the diagram shown above and set the values of the voltage sources,resistors as per the calculated values.<br>
2.Next go to SPICE Directive and type .lib filename.lib or .lib filepath.lib to import the Library file.<br>
3.Click OK, and place the generated command on the schematic.<br>
4.After importing the library file name the two mosfet as CMOSN.<br>
5.Set the channel length value of M1 as 180nm and we have to vary the value of the width to get a desired value of ID and Vout<br>
6.Repeat the same steps with M2 mosfet.<br>
7.Now go to Edit simulation command and select DC op pnt.<br>
8.Click OK, and place the generated command on the schematic.<br>
9.Next click on run button, you will get a pop up window which gives us information about operating point.It includes the values of Vout and ID.<br>

**Calculations**

The drain current with channel length modulation is expressed as:<br>
ID = (1/2)μnCox(W/L)(VGS - Vth)^2<br>
ITotal = P/VDD<br>
ITotal = Iref + Ix<br>
Since the ratio is 1:1 Iref = Ix<br>
Iref = ITotal/2<br>
ITotal = 1 mW/1.8 V<br>
ITotal = 0.555 mA<br>
Iref = 0.555 m/2<br>
Iref = 0.2778 mA.<br>
For matched transistors in a 1:1 ratio:<br>
W1/L1 = W2/L2<br>

![image](https://github.com/user-attachments/assets/64b19b43-49ae-4685-9ebe-72ac107809d8)

In order to determine the current value based on the specified ratio, the W/L values for M1, M2, and M3 are 10 µm/180nm, 10 µm/180nm, and 10 µm/180nm, respectively. Since Vin is chosen to be in the saturation range, the value that is provided is 0.6275V.<br>


**Transient Analysis**

**Procedure**

1.Change the input voltage to sine and change the amplitude to 50 mV , frequency to 1 kHz and offset voltage to 0.6275 V.<br>
2.Click on run command.<br>
3.Select transient analysis and choose 10 ms for stop time.<br>
4.Click on ok.<br>

![image](https://github.com/user-attachments/assets/860db9d5-f2ef-4778-8a03-353c1ea44f66)

![image](https://github.com/user-attachments/assets/3d286058-1ac1-4c4c-8edf-a3adccb54bf6)

**Result :**
The expected gain was greater than or equal to 10 V/V and the obtained gain is 13.77 V/V.<br>

**AC Analysis**

**Procedure :**

1.Change the Vin to AC and set AC amplitude to 1.<br>
2.Click on run simulation and choose AC analysis.<br>
3.Select type of sweep to decade , frequency range to 0.1 - 1 THz.<br>
4.Click on Ok.<br>

![image](https://github.com/user-attachments/assets/f2c0d3bc-1cd5-4fd0-9562-6bedf4932588)

**Result** : The Expected gain in dB is 20 and the obtained gain is 26.23 dB.<br>


| Parameter  | Theory Value | Practical Value |
| :---       |     :---:    |          ---:   |
| Av(in dB)  |     20dB     |    26.23dB      |  
| Av(in V/V) |      10      |     13.77       |

## 1:2 Ratio

**DC Analysis**

![image](https://github.com/user-attachments/assets/31237eef-a56d-4225-b2f4-8cd683ebb5a5)

As we know It=Iref+Ix

Therefore, for 1:2 aspect ratio 2*Iref=Ix

It = Iref + 2*Iref

So,Iref=It/3

It=P/Vdd

It=1mW/1.8V

It=0.555mA.

Therefore,Iref=0.185mA.

Here ,The aspect ratio of MOSFET M2 is twice of M3


![image](https://github.com/user-attachments/assets/1d3abfee-cdf6-46e3-b615-78d1214cb011)

In order to determine the current value based on the specified ratio, the W/L values for <br>
M2 and M3 are 6 µm/180nm and 6 µm/180nm<br>
M1 is 3 µm/180nm <br>
Since Vin is chosen to be in the saturation range, the value that is provided is 0.763 V. <br>

**Transient Analysis**

1.Change the input voltage to sine and change the amplitude to 50 mV , frequency to 1 kHz and offset voltage to 0.763 V.<br>
2.Click on run command.<br>
3.Select transient analysis and choose 10 ms for stop time.<br>
4.Click on ok.<br>

![image](https://github.com/user-attachments/assets/0d5a9efb-f6ab-453c-9b2d-de9ed8fd1372)

**Result :** The expected gain was greater than or equal to 10 V/V and the obtained gain is 12.11 V/V.

**AC Analysis**

1.Change the Vin to AC and set AC amplitude to 1.<br>
2.Click on run simulation and choose AC analysis.<br>
3.Select type of sweep to decade , frequency range to 0.1 - 1 THz.<br>
4.Click on Ok.<br>

![image](https://github.com/user-attachments/assets/b3cf8526-765b-4268-b3b9-c7598a70753d)

| Parameter  | Theory Value | Practical Value |
| :---       |     :---:    |          ---:   |
| Av(in dB)  |     20dB     |    25.57dB      |  
| Av(in V/V) |      10      |     12.11       |

Similarly,<br>

**For L=500nm**

| Ratio  |   Av(in dB)  |  Av(in V/V) |
| :---   |     :---:    |      ---:   |
| 1:1    |     11.15    |    14.9     |  
| 1:2    |     12.85    |    16.31    |

**For L=1um**

| Ratio  |   Av(in dB)  |  Av(in V/V) |
| :---   |     :---:    |      ---:   |
| 1:1    |     12.60    |    15.3     |  
| 1:2    |     9.55     |    15.98    |

## Inference

1.The current mirror circuit accurately copies the reference current with very little variation, ensuring reliable current mirroring across different W/L ratios.<br>
2.Even when the W/L ratio changes while keeping the same proportion, the drain current (ID) stays nearly the same, confirming the circuit's effectiveness.<br>
3.The amplifier gain is slightly higher than expected due to small differences in transistor properties or minor simulation effects.<br>
4.When the mirror ratio increases (from 1:1 to 1:2), the gain also increases as expected.<br>
5.Overall, the results closely match theoretical predictions, proving that the simulation and circuit design are working correctly.<br>

## Part B

**Aim** Design differential amplifie for following specifications Vdd=3.2V, P≤2.8mW, Vicm = 1.3V, Vocm = 1.7V, Vp = 0.6V. Perform DC analysis, transient analysis & frequency response and extract the required parameters.

**Circuit Diagram**

![image](https://github.com/user-attachments/assets/2ab2d8d1-555c-4416-891d-af2f7f444547)

**DC Analysis**

N-Channel MOSFETs: <br>
M1:	W=108.5 µm ;	L=180 nm<br>
M2:	W=108.5 µm ;  L=180 nm<br>
M3:	W=22.42 µm ;  L=180 nm<br>
M6:	W=10 µm    ;	L=180 nm<br>

P-Channel MOSFETs:<br>
M4:	W=52µm	; L=180 nm<br>
M5: W=52µm	; L=180 nm<br>
M6:	W=10µm	; L=180 nm<br>

![image](https://github.com/user-attachments/assets/0f832b8f-38e4-44b3-b734-ec0f0373995c)

**Transient Analysis**

![image](https://github.com/user-attachments/assets/3502a468-bf52-4310-9b3c-a28cb655b9f6)

A differential input of 10 mV peak, 1 kHz sine wave was applied to the gate of M1. Since the output of a differential amplifier is the difference in drain voltages of M1 and M2, only one side of the differential input was excited.

## Inference

The differential amplifier experiment highlights:<br>

The influence of channel length and W/L ratios on gain and bandwidth.<br>
The ability to customize circuit performance based on design goals by strategically selecting transistor geometries.<br>
The trade-offs between gain, bandwidth, and silicon area, which must be considered during analog circuit design.<br>



























