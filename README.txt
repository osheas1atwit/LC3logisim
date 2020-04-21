Welcome to the LC-3 in Logism!

This processing unit can perform basic arithmetic, logic, and memory operations. 
The following instructions are supported: ADD, AND, NOT, LD, LDR, ST, and STR. Here is an example list
of some pre-tested instructions that you can perform (in no particular order):

1401 = ADD R2, R0, R1
1883 = ADD R4, R2, R3

c000 = JMP R0

260a = LD R3 #10
6649 = LDR R3 R1 #9

3403 = ST R2 #3
778a = STR R3 R6 #10

To run any of these instructions: enter the 4-digit hex-code(s) into the RAM unit found in the
'main' circuit, enter values into the appropriate registers found within the 'Registers' circuit 
to be operated on, and begin ticking the clock. To restart the system, use the hand that allows 
you to change values (ctrl+1) and double click on the magnifying glass to enter the controlUnit. 
Within the controlUnit, reset the 'phaseCounter' and the register labeled 'PC' to 0 and then
you're good to go.

To note when using this processor: any ST instruction (not STR) should use an offset value of one-
less than the offset that would get to the address you want to store at. The order in which the phases
change data causes the 'pcSelector' to receive an already-incremented PC value, so when the offset is
added during phase 3, the destination value is written one spot above the originally intended address.
Also, if the Logisim gives a 'label collision' error when loading the circuit, just rename any of the
tunnels that output blue wires in the 'main' circuit to 'clock'. Lastly, this .circ was made with the
.jar version of Logisim, not the Windows .exe version of the software. Otherwise, everything should work
as intended.

All of the tests listed above were previously tested with various register values and proved to work
as intended. The AND and NOT operations were also tested early in the building process and once the
ALU was completed it has not been modified so there was no reason to retest. The LD and LDR operations 
properly read from the address instructed and store to the correct register, ST stores the value found
within the source register but the offset needs to be subtracted by one to store to the proper address,
and STR stores the value found within the source register to the intended address without any 
accommodations to the offset or base register. Since all of these worked as intended, I came to the 
conclusion that they were good tests. I also ran a string of instructions in a row that read a value,
added two values together, jumped ahead 30 addresses, and then stored a value 3 addresses ahead of the
PC, and after several full phase cycles the PC incremented properly up to the stored value from the 
store address. Everything worked as far as I could tell and I think that these are good tests for the
instructions.

All circuits were designed to be easy to follow and feature documentation describing some of the specific
aspects of the system. 
