---
title: "OpenOffice Calc formula needed"
date: 2013-01-29
forum: Desktop Environments
---

### Post by faizlo on 2013-01-29
Hi all,

I am sorry for my naive question but I really need help.
I have a spreadsheet which has 3 sheets in it.
This is a spreadsheet for students grades. the second sheet is for students attendance, which I want to link to their grades in the first sheet.
What I want is this:
Since all of the 3 sheets have the same set of names, then if a student gets a grade (greater than 0) on the first sheet, a letter "S" is to be shown in the corresponding cell in the second sheet.


How may I do this?

Thank you in advance,

~faizlo

---

### Post by sanderj on 2013-01-29
Easy:

=IF(Sheet1.B2>0,"S","")

With in Sheet1 on location B2 the grade.

---

### Post by SeijiSensei on 2013-01-29
I'll just note didactically that that method works only if the lists are identical and sorted identically.  There are also "lookup" functions that can look in one table and return a value that corresponds to a match between a criterion and the "keys," in this case the names, that define the entries in the table.  Of course, this relies on the names being identical.

---

### Post by faizlo on 2013-01-29
Perfect, it worked like a charm!
Now another question:
How may I do this to all cells in the same column? I tried to highligh the first cell, and drag to include all cells below it (The same column) but my coloring scheme went away... Is there away to do it without changing the formatting?

One other question, please:
How may I add two conditions or more? (as in >0)?

Thanks again,

~faizlo

---

### Post by sanderj on 2013-01-30
Both are basic questions. So probably better to start some self-learning: read the OpenOffice help, a webpage or a book.

Good luck!

---

### Post by faizlo on 2013-02-01
Hi

Thank you for the advice.
My problem is that this is a first time I use excel. I use many different stuff in my work. But it is my first time to teach and be asked to use excel.
I will see what I can do and come back again.

Thanks for the help.

~faizlo

---

### Post by ugm6hr on 2013-02-02
> **faizlo said:**
> 
How may I do this to all cells in the same column? I tried to highligh the first cell, and drag to include all cells below it (The same column) but my coloring scheme went away... Is there away to do it without changing the formatting?
Use the "Paste Special" option instead of "Paste" - I think it is Ctrl+Shift+V keyboard - and select "formula" only

> **faizlo said:**
> 
How may I add two conditions or more? (as in >0)?
This doesn't make sense to me. The ">0" is a correct condition.

---

### Post by SeijiSensei on 2013-02-02
Multiple conditions usually require nested IFs:

```
=if(a1>0,if(a2>0,"bothpos","not"),"not")
```

returns "bothpos" if both a1 and a2 are positive, and "not" otherwise.

---

