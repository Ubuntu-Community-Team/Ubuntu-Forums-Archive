---
title: "open office.org calc #DIV/0"
date: 2009-02-08
forum: General Help
---

### Post by M0GEJ on 2009-02-08
Hello,
I am trying to do a simple spreadsheet on calc. In one cell I have the formula =(C2*D2)/(E2/F2) but I get #DIV/0 when I try this. All of the cells have values in them > 0, but I notice when I try and copy the columns with calculations involving powers in to another part of the spreadsheet the values returned are 0. This includes the J column, but I am a little confused as when I copy columns involving simple addition sums the values get copied. Any ideas??

---

### Post by SteveDee on 2009-02-08
> **M0GEJ said:**
> Hello,
I am trying to do a simple spreadsheet on calc. In one cell I have the formula =(C2*D2)/(E2/F2) but I get #DIV/0 when I try this. All of the cells have values in them > 0, but I notice when I try and copy the columns with calculations involving powers in to another part of the spreadsheet the values returned are 0. This includes the J column, but I am a little confused as when I copy columns involving simple addition sums the values get copied. Any ideas??

Not absolutely clear on your problem. I copied your formula (above) and pasted to cell A1 in Calc. If E2 or F2 is 0 I get #DIV/0 error, otherwise OK.

If I copy & paste the formula from A1 to say G1, the formula is modified by the new location. So =(C2*D2)/(E2/F2) becomes =(I2*J2)/(K2/L2). The new locations are relative to G1 just as they were to A1.

Try using Paste Special to see exactly what you are asking Calc to do.

---

### Post by M0GEJ on 2009-02-09
Well basically one of the columns in my table was for radius^4.This column retured values, but when I tried copying these cells, the posted cells only showed a 0 in them. This was not the case with other columns containing simple calculations (additions). So firstly I was wondering why I can't seem to cut and paste to work with cells containing powers calculations. Secondly I was wondering if the fact that whenever I try to reproduce these values I get 0 is leading to the #DIV/0 error.

The box ticked in paste special is to "paste all"

---

### Post by lavinog on 2009-02-09
how is radius referenced?
are you using something like A3^4
if so copying and pasting it is going to change the cell that radius refers to...ie: if B6 contains the above formula and you copy and paste it into C7, C7 will equal B4^4.
This is normal behavior and to prevent it from doing this you have to change your original formula to $A$3^4.  The $ tells the spreadsheet to hold that position.

As for the div/0 errors...there is a minimum tollerance with values really close to 0.
a formula such as (C2*D2)/(E2/F2), where F2 is a really big number can yeild a div/0 error.

Is this file something you can share, or can you make a new example file?

---

