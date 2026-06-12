---
title: "How to install HoN on ubuntu jaunty ?"
date: 2009-07-24
forum: Gaming &amp; Leisure
---

### Post by born2rule on 2009-07-24
Hi all !
I`m very new to ubuntu, and i would like to play HoN, i have an acount, i dl the file for linux and it is in a ( ...sh form). I don`t know what to do with it (i`m a total noob with linux). Can someone post some idiot proof instructions on how to install this game? 

Thank you !

---

### Post by Grenage on 2009-07-24
I think you make it executable: chmod +x game.sh

Then run it as a normal script: ./game.sh

---

### Post by Bölvaður on 2009-07-24
> **Grenage said:**
> I think you make it executable: chmod +x game.sh

Then run it as a normal script: ./game.sh

that is correct.

Here is another version of doing the exact same thing (except this is just clicking with mouse)


Right click on the .sh file
Click **Properties**
Find a tab named **Permissions** in the window that will pop up
Click the box in the middle here: Execute **[]** Allow executing file as program
Click **Close**
Double click the .sh file


If I remember correctly this is exactly how I did it.

---

### Post by badrra on 2009-09-19
it is saying "illegal Instructions" any idea on this one?

---

### Post by Vadi on 2009-09-19
corrupted download - redownload the file then

if you still get it, in the terminal, do "md5sum <file>" of the installer and see what number do you get

---

### Post by badrra on 2009-09-22
> **Vadi said:**
> corrupted download - redownload the file then

if you still get it, in the terminal, do "md5sum <file>" of the installer and see what number do you get


md5 is correct. I reported the problem to HON awaiting their response.

---

### Post by bartos on 2009-09-24
I installed mine with ```
sh HoNfile.sh
```
Check menu under games after install

Have fun

---

### Post by badrra on 2009-09-25
same thing. illegal instruction

HoN has not answered me yet. I Tried hardy but still doesn't work.

---

### Post by oldrocker99 on 2009-09-26
Do note that HoN doesn't allow a sudo installation; just one that goes into your home folder.

:guitar:

---

### Post by dagoth_pie on 2009-09-26
> **oldrocker99 said:**
> Do note that HoN doesn't allow a sudo installation; just one that goes into your home folder.

:guitar:

Also to anyone watching, keep in mind that this is the temporary workaround while it's in beta, and they do plan on making it a system wide installer when it's released.

---

### Post by ShannonMcC on 2012-09-11
> **Bölvaður said:**
> that is correct.

Here is another version of doing the exact same thing (except this is just clicking with mouse)


Right click on the .sh file
Click **Properties**
Find a tab named **Permissions** in the window that will pop up
Click the box in the middle here: Execute **[]** Allow executing file as program
Click **Close**
Double click the .sh file


If I remember correctly this is exactly how I did it.

This worked perfectly, yes years later but it still helped! Thanks.

---

