---
title: "WINE help - plz"
date: 2006-02-18
forum: Desktop Environments
---

### Post by s_h_a_d_o_w_s on 2006-02-18
I have installed wine with automatix. HOw do i get it to run from there? 

(i think i need to enter a command, but i'm not sure)

plz

---

### Post by FizDev on 2006-02-18
You can or associates the *.exe with the wine application or go into the terminal, to the directory of the .exe you want to run and then type
> wine nameoftheexe.exe

To associate it, you can 
Right-Click on a *.exe
then choose : "Open with Other Application"
then choose : "Use a custom command" and enter "wine"

---

### Post by nalmeth on 2006-02-18
hit alt-F2, then type in the command "winecfg".
This will allow you to setup wine the way you want, and will create your virtual windows system (/home/username/.wine). To see the wine folder in nautilus, go to your home folder, and go VIEW --> Show Hidden Files

---

### Post by s_h_a_d_o_w_s on 2006-02-18
thx, but how do I run games? do I open wine then run cd?

---

### Post by tanman on 2006-02-18
I also do not understand how to work with wine. I have downloaded psp video9 using wine and I can find the program folder, but how do I actually get something to run. Do I have use winecfg and then find it through there? Really confused on this one. Thanks for any help.

---

### Post by nalmeth on 2006-02-18
If you've run winecfg, you should be set to use wine for any .exe
right click on the .exe, and tell it to run with wine
if this option does not appear, click 'open with' and enter the command 'wine'

Check winehq.com to see if your software is supported by wine aswell. It's a great compatibility layer, but it does not run all windows apps. It's quite a work in progress for wine devels

EDIT I misread you guys a bit there! To actually run the thing, open nautilus, go to your home directory, and go VIEW --> SHOW HIDDEN FILES
find the .wine folder, and see your virtual windows system, program files and all

or, hit alt-F2, and type nautilus /home/username/.wine 
username being, your, username.. of course..

---

### Post by s_h_a_d_o_w_s on 2006-02-18
Do i need to install it first?

---

### Post by albertobob on 2006-02-20
I think i delete a folder in the winefile file browser.  I am unable to find the folder anywhere, I was wondering if anyone knows where a folder would go if it was deleted in winefile.  Does it go to a sort of holding area, such as the trash can, or is it completely deleted?

---

