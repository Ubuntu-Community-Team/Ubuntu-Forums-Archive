---
title: "OpenOffice 3.0 SUMIF Problem"
date: 2009-05-20
forum: General Help
---

### Post by eekfonky on 2009-05-20
Hello

I went to the OpenOffice forum and was told that the issue I'm having is due to ubuntus version of OpenOffice. Why is it different to the rest? I would use the deb version from the OO website but I need my spreadsheet to work on ubuntu as I share the workbooks with other parties who don't want to remove the ubuntu version. Please help.

I'm using SUMIF and get error codes where I shouldn't.

=SUMIF(A5-I5,">0") err:504
=SUMIF(A5-I5;">0") err:508

neither works. why?

---

### Post by Oats on 2009-06-20
I've come across the same problem.  I'd like to use this function and now I'm curious about the nature of the problem.  Why does the Ubuntu version of OpenOffice differ from the regular version?

---

### Post by Oats on 2009-06-20
> **eekfonky said:**
> 
error codes where I shouldn't.

=SUMIF(A5-I5,">0") err:504
=SUMIF(A5-I5;">0") err:508

neither works. why?

Try this:
=SUMIF(A5:I5, ">0")

I think the err:504 is because you used - to denote range instead of :.

However, I still get err:508 with the following:
=SUMIF(A5:I5;">0")

According to the documentation, the semicolon should be fine.  I haven't figured this one out yet.

err:508 is given if I use semicolons instead of commas in AND, IF, etc.  Although the documentation shows that semicolons may be used.

---

### Post by eekfonky on 2009-06-20
I wasn't denoting a range, I wanted to do a minus. I can only assume it's impossible. Thanks anyway

---

### Post by Vaphell on 2009-06-20
Well, this doesn't work in my OO v2.4 in Hardy

I am curious why would you want to use minus? sumif with 2 params requires cell range and condition. Is cell1-cell2 supposed to be a cell range?

---

### Post by eekfonky on 2009-06-20
I needed a stock control. So cell 1 = stock and cell 2 = order. I needed that condition. I have figured it out with IF function. It's not pretty but it works

---

