---
title: "Changing the default option in GRUB"
date: 2005-08-18
forum: Desktop Environments
---

### Post by masterkale on 2005-08-18
I installed kubuntu on a second harddrine in my Window$ machine, which is used by my whole family. And when GRUB was installed the default start was Kubuntu. How do I change GRUB to highlight Windows and start windows if there is no user interference? Thank you for your help. I did this once before in SuSE useing YaST but there is no YaST in Kubuntu.

---

### Post by jerrykenny on 2005-08-18
Masterkale,   open a Konsole,  or other terminal . . . 

type                         sudo kedit /boot/grub/menu.lst

change the line      Default    0

to                            Default    1



actually if "kedit"   doesnt work, tthen try "kate"   or lastly  "nano"

---

### Post by masterkale on 2005-08-18
Hey, Thank you for the help. I am away from my machine right now, but I will post back when I get it.

---

### Post by masterkale on 2005-08-18
I changed the default to 1, but that only made it select one down, which makes sensse, so it was slecting recovery mode.
I need to change it to 4 for windows. When I do the same command in terminal, i just get a blank section, and then the options at the bottom. I just tried it with the xorg.conf file to see if it works, and it does the same thing. I can navigate to the files and read then, i just can't edit then, and every time I try to use sudo in the terminal the files ar blank, and I can't edit them. Also I noticed after I restarted to see if it changed that when booted into Kubuntu it has to fix an error and restart. and then it will work. I have tried this twice now, and it has the error then restarts after it fixes it and works fine. Also there is a backup menu.lst~ how do I go about making that the main file. Since this is what caused the problems maybe it will fix them.

Thank you for your help.

---

### Post by masterkale on 2005-08-18
I got it, I just had to go into command line, and do it there. But that still brings up the question why I can't do it in the Konsole

---

