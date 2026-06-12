---
title: "[SOLVED] screen capture help"
date: 2007-08-27
forum: Desktop Environments
---

### Post by tropcky on 2007-08-27
hi evry one  i just need help in the screen capture in ubuntu 
i know that i start with 
sudo apt-get install recordmydesktop                to install it 
then  i do 
recordmydesktop                to make it start 
and it start and ery thing  is so cool 
but how can i make it stop and save it  
thank u all 
tropcky






ubuntu forums = great help great ppl nice forums           happy to be a member in it

---

### Post by Chymera on 2007-08-28
the program minimizes itself to a tray icon (a gray square) click on it, and it will stop and start encryption.
Do not close the window during encryption! 
Unles you set it otherwise, the .ogg should be saved in your home directory

---

### Post by tropcky on 2007-08-28
thank u so much man  really thanks

---

### Post by tropcky on 2007-08-28
oky 
i trayed  2 run it agen but i cant see any icon on tray i dont see the icon any wher

---

### Post by Chymera on 2007-08-28
I didn't quite understand that... would you mind describing exactly what you did?

---

### Post by tropcky on 2007-08-28
will i start with 
recordmydesktop
and its start capturing 
u told me that it will be icon in the try  to stop 
but i didnt faind any icon

---

### Post by tropcky on 2007-08-28
guys   guys i need a little help here oky so plez tell me how can i do 
screen capture  video 4 sure 
thank u

---

### Post by tropcky on 2007-08-29
hello 
so plez help 
thank u

---

### Post by Chymera on 2007-08-29
hmmm... i really dont know, if you clicked the record button then that icon should be in the tray list (usually in the upper right corner of the screen).

---

### Post by tropcky on 2007-08-29
look man ther is no record button its only  u type 
recordmydesktop  and its starts recording  
so i cat see ant tray icon any wher

---

### Post by tropcky on 2007-08-29
dont forget me guys 
look if ther is np hop to capture screen by thes way   plez tell me anther way or a program 2 use 
thank u

---

### Post by iovar on 2007-08-29
tropcky, recordMyDesktop is a commandline program. If you want to use it through 
a graphical user interface, you must install and run gtk-recordMyDesktop which is also 
available in ubuntu's repositories.

In order to stop recording on the console, press control-c. You can find out more about
CLI (commandline interface) usage of recordMyDesktop with this command, on a terminal window:

**~$ man recordmydesktop **


Notice that after you install gtk-recordMyDesktop, you will be able to start it from your programs
menu, presumably in the multimedia category.



Also if you had previously abnormally terminated recordMyDesktop, you may have
leftover files, needlesly occupying space in you hard disk. So go to the 
/tmp directory and delete all subdirectories named rMD-session-*some number"
Make sure when doing this to not have any running instances of recordMyDesktop.

---

### Post by tropcky on 2007-08-29
oky itrayed   but take a look of that 

^[[Atropcky@tropcky-linuxsudo apt-get install gtk-recordmydesktop
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Crisco on 2007-09-04
Regarding the Recordmydesktop stopping issue, I ran it through the terminal and when I wanted to finish recording I just pressed Ctrl+C and it stopped recording and began to encode the file.  Hope that helps

---

### Post by tropcky on 2007-09-04
thank u so much thank u

---

