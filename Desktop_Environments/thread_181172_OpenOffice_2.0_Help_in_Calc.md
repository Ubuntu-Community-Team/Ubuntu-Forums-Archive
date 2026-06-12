---
title: "OpenOffice 2.0 Help in Calc"
date: 2006-05-23
forum: Desktop Environments
---

### Post by interse on 2006-05-23
I want to type   ACN  in a cell, as an acronymn.  No matter, if I type it in lowercase or upper case, ACN is automatically changed to   can   .  If I type  'ACN  the same thing occurs.  

One way to avoid the automatic change is to type a period after the three letters, as in  ACN.    

What is causing this?  What is  ACN  in OpenOffice Calc that 'causes' it to be immediately changed to   can    ?

Can I override the change?

---

### Post by Phlosten on 2006-05-23
That would be automatic spelling correction. 

Select 'Tools' -> 'Options'. Expand the 'Language Settings' bit. Select 'Writing Aids'
Under 'Options' unselect 'Check spelling as you type'.

Hopefully that sorts the problem out.

---

### Post by SavageBeginner on 2006-05-23
This worked for me:

Click 'Tools'->'AutoCorrect'
On the 'Options' tab uncheck 'Use replacement table'

---

### Post by npodges on 2006-05-23
tools> autocorrect

from there, you can choose to turn off autocorrect, or remove the entry that changes ACN to CAN

edit: oops.

---

### Post by interse on 2006-05-23
Thanks everyone!   For everyone's information: Unchecking  'Check spelling as you type' and/or 'Autocorrect Spelling'  do not work in this instance   ACN.

What did work was Unchecking  'Use Replacement Table'   

Again, thanks to all.  Problem solved.

---

