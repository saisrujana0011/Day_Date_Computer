# Day_Date_Computer
With the circuit described here one can easily find out the day for any date within 1901 to 2000 AD.

This circuit is basically an adder, built around 1C7483 (adder), 1C74195 (shift register) and IC74147 (priority encoder). IC7445 is used for input and output.

CIRCUIT DESCRIPTION:

IC74147 converts currents input from switches (S0-S7) into their binary equivalents. Output from IC74147 is given to the IC7483.


![image](https://user-images.githubusercontent.com/91731751/166444612-f049f497-9b1a-4e97-877d-499080b4f91b.png)

IC7483 adds the given binary input from encoder with the contents of shift register 74195 (parallel in parallel out shift register). When enter key is pressed, the sum output from IC7483 is transferred to the shift register. Hence, next input is added with the previous sum. In this way circuit performs serial addition. IC7445 decodes the output of shift register. LEDs 1 to 7 indicate the days from Sunday to Saturday respectively. Before entering the next set of data,the contents of shift register 
should be made zero, i.e. the LEDs must be in off sate.Contents of shift register can be cleared by pressing reset switch (S9).

The switches (S0-S7) corresponding to codes for date,month,year are listed in the Table II .Their codes are convertd into binary equivalents by encoder.

![image](https://user-images.githubusercontent.com/91731751/166444755-672f208f-5b1a-4f3e-af6e-ff2609978f67.png)

Adder adds the binary input from encoder with the contents of shift register (initially 0). If the sum exceeds 7,then 7 should be subtracted from the sum.This can be easily done by connecting MSB of sum(pin 15 of IC2) to carry-in input(pin 13 of IC2).MSB is 1 for sum>7 and hence 1 is added to the output of sum.
Only 3 bits of output are taken from the adder.Therefore, output is always less or equal to 7.
The sum output from adder is transferred to parallel-in-parallel-out shift register.The output from adder is transferred to parallel in parallel out shim
register. The output of shift register is connected to input of the adder and the decoder IC7445. Shift register copies the sum output when clock input goes from high to low state. This clock input is given using switch S8. The next input data is added with previous data input.

![image](https://user-images.githubusercontent.com/91731751/166444869-39154744-b74e-4a7a-9a47-b7d3c1a8b2c4.png)

![image](https://user-images.githubusercontent.com/91731751/166444961-86bfd966-4313-4a1e-8314-c027448577d0.png)

Decoder converts the binary to respective decimal equivalent and corresponding LED glows indicating the day.

Priority encoder produces 4-bit BCD for corresponding decimal input but actually one's complement of input is generated. In this particular circuit only 3-bit output is needed hence input switches can be selected so as to get the necessary output.Owing to switch debounce problem, in clock input, a switch debouncer using NAND gate is used between switch S8 and clock input of shift register.

PRINCIPLE:

Basically the circuit performs only addition and it is possible to find out day by adding codes for year, month and date. Code for year is given in 
Table I. Codes for month and date are given in Table III. Foe example, consider a date 27/1/1971. To find the day on this date, find out the code for the year 1971 from Table I.Code for year is D, which is equal to S (from Table II). Code for the month January is 1 and for date 27, it is 5 (Table II). Sum of all these codes is equal to 11. Since 11 is greater than 7 (total no. of week days), subtract 7 from 11. We get 4, which in¬dicates that LED4 is glowing which stands for Wednesday (Table IV).

WORKING:

To find out the day for any date, codes for year, month and date are entered one by one.
The circuit is reset by pressing the reset switch momentarily. Then find out the code (A-G) for particular year from the Table I. Switch in corresponding to the code is pressed, then enter key (S8) is pressed.All the switchs are then restored to normal position. Now the circuit is ready to accept next data (i.e,month).Code for the month is given in Table III. Switch to be pressed for a particular month is given in Table II. Switch corresponding to the month is pressed followed by enter key (S8). In the same way, date is entered.The glowing LED indicates the day after the date has been entered. To enter the date 27-01-1971 following sequence of switches will be pressed.

For year 1971, code is D (from Table I). To enter D, press switch S5. Then press enter key S8. Restore switches S5 and S8 to normal position. For month, refer Table II. For January, switch Si is pressed and then enter key, S8 is pressed. Switches S1 and S8 are restored to normal position.To enter the date 27 refer Table II.For 27,press witch S5 and then S8.Now restore switches S5 and S8 to normal position.

The LED corresponding to wednesdat starts glowing. The circuit must be reset before entering next date.Therefore, for the date 227-01-1971 ,sequence of keys are S5,S8,S1,S8,S5 and S8.










