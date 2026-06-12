---
title: "Code for myself"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by PToros on 2007-10-19
Hey, this is a post for myself in order to copy code because my flash drive is MIA.

 import java.util.Scanner;
 
 public class PrimeNumber
 {
 	public static void main(String[] args)
 	{
 		Scanner input = new Scanner (System.in);
 		
 		int number, remainder, prime;
 		final int LIMIT = 1;
 		
 		do
 		{
 			prime = 1;
 			System.out.println("");
 			System.out.println("Enter a number greater than 1. Enter 1 to exit.");
 			number = input.nextInt();
 			
 			if (number < 2)
 				System.out.println("Invalid Number");
 			if (number > 1)
 			{
 				for (int count = number - 1; count != LIMIT; count--)
 				{
 					remainder = number % count;
 					if (remainder == 0)
 					{
 						prime = 2;
 					}
 				}
 			
 			if (prime == 2)
 				System.out.println("The number " + number + " is not prime.");
 			if (prime == 1)
 				System.out.println("The number " + number + " is a prime number.");
 			
 			}
 		}
 		while (number != 1);
 	}
 }





import java.util.Scanner;
 
 public class Mod
 {
 	public static void main(String[] args)
 	{
 		Scanner input = new Scanner (System.in);
 		
 		int number, number2 = 1, remainder, prime = 1, temp;
 		final int LIMIT = 1;
 		
 		do
 		{
 			System.out.println("");
 			System.out.println("Enter 2 numbers greater than 1. Enter 1 to exit.");
 			number = input.nextInt();
 			
 			if (number !=1)
 			{
 				System.out.println("Enter the second number.");
 				number2 = input.nextInt();
 			}
 			
 			if ((number < 1) || (number2 < 1))
 				System.out.println("Invalid Number");
 			if ((number > 1) && (number2 > 1))
 			{
 				if (number2 > number)
 				{
 					temp = number2;
 					number2 = number;
 					number = temp;	
 				}
 				
 				for (int count2 = number; count2 != number2 - 1; count2--)
 				{
 					prime = 1;
 					for (int count = count2 - 1; count != LIMIT; count--)
 					{
 						remainder = count2 % count;
 						if (remainder == 0)
 							prime = 2;
 					}
 			
 					if (prime == 2)
 						System.out.println("The number " + count2 + " is not prime.");
 					if (prime == 1)
 						System.out.println("The number " + count2 + " is a prime number.");
 			
 				}
 			}
 		}
 		while (number != 1);






import java.util.Scanner;
 
 public class DigitSum
 {
 	public static void main(String[] args)
 		{
 			int number,thousands, hundreds, tens, ones, total;
 			
 			System.out.println("Enter a positive integer less than 10,000:");
 			Scanner input = new Scanner(System.in);
 			number = input.nextInt();
 			
 			if ((number > 10000) || (number < 1))
 				System.out.println("Invalid number.");
 			else
 			{
 				thousands = number / 1000;
 				number = number % 1000;
 				
 				hundreds = number / 100;
 				number = number % 100;
 				
 				tens = number / 10;
 				number = number % 10;
 				
 				total = thousands + hundreds + tens + number;
 				System.out.println("The sum of the digits is " + total);







public class XMas
 {
 	public static void main(String[] args)
 		{
 			int count;
 			count = 1;
 			String suffix;
 			
 			while (count <= 12)
 			{
 				switch (count)
 				{
 					case 1:
 						suffix = "st";
 						break;
 					case 2:
 						suffix = "nd";
 						break;
 					case 3:
 						suffix = "rd";
 						break;
 					default:
 						suffix = "th";
 				}
 				
 				System.out.println("On the " + count + suffix + " day of Christmas my true love gave to me");
 				
 				switch (count)
 				{
 					case 12:
 						System.out.println("Twelve drummers drumming,");
 					case 11:
 						System.out.println("Eleven pipers piping,");
 					case 10:
 						System.out.println("Ten lords a leaping,");
 					case 9:
 						System.out.println("Nine ladies dancing,");
 					case 8:
 						System.out.println("Eight maids a milking,");
 					case 7:
 						System.out.println("Seven swans a swimming,");
 					case 6:
 						System.out.println("Six geese a laying,");
 					case 5:
 						System.out.println("Five golden rings,");
 					case 4:
 						System.out.println("Four calling birds,");
 					case 3:
 						System.out.println("Three french hens,");
 					case 2:
 						System.out.println("Two turtle doves, and");
 					case 1:
 						System.out.println("A partridge in a pear tree.");
 				}
 				count++;

---

### Post by Sockerdrickan on 2007-10-19
wtf? wrong section

---

### Post by cogadh on 2007-10-19
Depends on what that code does....

---

### Post by Sockerdrickan on 2007-10-19
No there's a programming section.

---

### Post by cogadh on 2007-10-19
I was kidding. Sorry, I should have put the <sarcasm> tags on the post.

---

### Post by Sockerdrickan on 2007-10-19
hahahaha xD

---

