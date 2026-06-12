---
title: "How to import into OpenOffice Base?"
date: 2006-04-05
forum: Desktop Environments
---

### Post by pmilin@ptt.yu on 2006-04-05
Dear ALL,
I cannot figure out how to import, for example, Access' mdb file, or even a table into the OpenOffice Base. Can somebody help me with this issue? Access is one of the two things that sticks me with the MS Windows. The other is MS Visual C++. And as Bono Vox pointed out: 'I still havn't found what I am looking for', regarding IDE's for C++ and database manipulation. 

Sincerely,
P. Milin

---

### Post by localzuk on 2006-04-05
> MS Visual C++

C++, I find, is easiest to code using a simple text editor and a terminal window. I have always found IDE's to be intrusive and distracting - and therfore reduce my productivity. How do you find that the IDE helps you? What advantages does it give you?

---

### Post by MartinG on 2006-04-05
[QUOTE=pmilin@ptt.yu]I cannot figure out how to import, for example, Access' mdb file, or even a table into the OpenOffice Base. Can somebody help me with this issue? [/QUOTE]I used to access mdb files from OpenOffice.org 1.1.4, via ODBC or JDBC, so I'm sure it must be possible with OOo2.  You may have to install the driver packages first, such as unixodbc, but once you've got that right it's just a matter of starting Base and picking the right options in the Open wizard.  

For another approach, have you looked at mdbtools and mdbtools-gmdb, which may be an alternative route to access the data and transfer it?  Or could you export it direct from Access?

Sorry I can't give a step-by-step, but I no longer have an mdb file available to experiment on ;)

---

### Post by yellowstar5 on 2006-04-05
One way to get your TABLES is to export them from Access to Excel spreadsheets or csv

Then open them in OO Calc, and cut and paste into a new table in Base.  You have to note the difference between selecting the whole spreadsheet in one go by selecting the top left corner cell (of border not cell A1) or by selecting the data by dragging over the whole range (top left to bottom right cell).

One way you can't then add further records to the table in base, the other you can.  Or at least that's my experience.

Reports, queries or code would be another item.

---

### Post by cobolt01 on 2008-05-26
> **localzuk said:**
> C++, I find, is easiest to code using a simple text editor and a terminal window. I have always found IDE's to be intrusive and distracting - and therfore reduce my productivity. How do you find that the IDE helps you? What advantages does it give you?

I like IDEs because they colour text so that it's more readable and help you format text quickly and easily. Big IDEs are horrible though. For a Java IDE on windows I've found that JCreator is very nice. I haven't done much java programming on Linux and when I did I encountered problems with Swing.

---

