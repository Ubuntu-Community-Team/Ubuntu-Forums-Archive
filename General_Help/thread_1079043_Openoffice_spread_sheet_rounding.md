---
title: "Openoffice spread sheet rounding"
date: 2009-02-24
forum: General Help
---

### Post by RealG187 on 2009-02-24
I am making a spreadsheet and it keeps rounding to the lower whole number. I added the decimal places but it just adds zeros, ex 53.00 instead of 53.34..

How can I make it show the exact value, in excel there was an option for this somewhere, but I can't find it here...

---

### Post by SteveDee on 2009-02-24
> **RealG187 said:**
> I am making a spreadsheet and it keeps rounding to the lower whole number. I added the decimal places but it just adds zeros, ex 53.00 instead of 53.34..

How can I make it show the exact value, in excel there was an option for this somewhere, but I can't find it here...

If you right click the cell then "Format cells..." what format type do you have? If you select the required Number format it should give you just what you want.

---

### Post by RealG187 on 2009-02-24
I have tried number format and currency format but it always rounded the number off, even when I added more deciaml places, it just added 0's after the decimal point...

---

### Post by todak on 2009-02-24
**Format> Cells...** Under the **Options** line is a selector for **Decimal places**. Choose how many decimal places you need and watch the example numbers change for you.

---

### Post by RealG187 on 2009-02-24
If I add so there are two numbers after the decimal is just says:

53.00 when the exact number is 53.34. Adding decimal places does not help, it just adds insignificant zeros after the decimal...

---

### Post by RealG187 on 2009-03-04
Koffice does this too, I if say it's $5 an alltogether and there are two items (so divide 5 by 2) it says the cost of one item is $2.00 when it actually is $2.50

---

### Post by RealG187 on 2009-03-05
Attached I have posted an example of what I mean, I took $5 and divided it by 2 and it says $2.00 not $2.50!

(Remove the .zip, I had to rename it to .zip so I could attach it)

---

### Post by SteveDee on 2009-03-06
> **RealG187 said:**
> Attached I have posted an example of what I mean, I took $5 and divided it by 2 and it says $2.00 not $2.50!

(Remove the .zip, I had to rename it to .zip so I could attach it)

The expression you have in C1 is: =QUOTIENT(A1;B1)
This returns the integer number of the division A1/B1 {hence the result=2}

I'm guessing you didn't use this intentionally. Take a look at the attached (again, just remove the .ZIP suffix and open in OpenOffice Calc). You should see the correct result in C2 (unless your OO Calc is screwing things).

I also noticed that when I saved my changes, it asked if I wanted to save as OpenOffice 1.0 Spreadsheet format. I'm using OpenOffice V2.4.

I hope this helps.

---

### Post by RealG187 on 2009-03-06
What do you mean integer, wouldn't 2.5 be the integer, how would it get 2?

I think I made that spraedsheet in Koffice (I wanted to see if I could get it to do it the way I want) and I saved it, I guess Koffice saved it as open office 1.0

If I put in =A1/A2 will MS Excel understand that (or other Spreadsheet software)

---

### Post by SteveDee on 2009-03-07
> **RealG187 said:**
> What do you mean integer, wouldn't 2.5 be the integer, how would it get 2?

I think I made that spraedsheet in Koffice (I wanted to see if I could get it to do it the way I want) and I saved it, I guess Koffice saved it as open office 1.0

If I put in =A1/A2 will MS Excel understand that (or other Spreadsheet software)

An integer is any whole number (e.g. 2, 7, 120). Real numbers may include a decimal point (e.g. 2.5, 1.763, 120.95).

In Open Office Calc or MS Excel, if you click on a cell and type:  =A1/B1
you get the division of the value in A1 by the value in B1, as a real number. So in your example: 5 divided by 2 = 2.5

The strange thing about your spreadsheet is that it is using the "Quotient" function, (which means the result is 2.5, but it throws away the .5 and just displays the integer 2). 

According to the help file, this "Quotient" function is only available if you have the "Analysis Addin" installed. Even if it is installed, I would not expect this to be used unless you had called it up somehow.

In Open Office or KOffice I suggest you try again and type: =A1/B1   in cell C1 and see if it works. If not, click on C1 to read its contents.

I hope this helps.

---

