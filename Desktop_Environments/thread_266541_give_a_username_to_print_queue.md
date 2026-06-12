---
title: "give a username to print queue"
date: 2006-09-27
forum: Desktop Environments
---

### Post by nofrak on 2006-09-27
I'm at a college (duke) with a central printing system you can use from any computer or your own system that associates your jobs with your username, so that you can collect them later.  In Windows and Mac, you have a program to set up this printer, but Linux is unsupported officially.  They give you the info you need to set up the printer, but all they tell you after that is that you need to add the -U flag to the lpr command and then your username.

That works just fine for the command line, but I can't figure out how to give a username when printing from, say, Firefox or OpenOffice.org, etc.  This is one of my very few remaining annoyances with Ubuntu, so I'd love to be able to get this working!

---

### Post by nofrak on 2006-09-27
if you think there's no solution, say that too, so that I can resign myself to it.

---

### Post by nofrak on 2006-10-06
So after much documentation and soul searching, I found the answer while trying to figure out something totally different.  In the print dialog, if you click the "Print to file" box, and then edit the printer preferences, you can edit the command.  You probably have to do this for each of your programs, but it sure beats creating a .ps file and printing from the command line each time.

---

