---
title: "no desk top"
date: 2006-06-10
forum: Desktop Environments
---

### Post by tnlogger on 2006-06-10
I just installed dapper with a complete install I can log in and the desk top
will not boot. all I get is the command promt. I have read all the help and documents on line but still can't get it to boot to the desk top.
 just to let you know I have never used linux before. So it might be me ;) 
 thanks in advance gene

---

### Post by ayoli on 2006-06-10
not vry precise ... did you have a look on logs (in /var/log) ?
maybe an X error or misconfig, if it is you can try:
sudo dpkg-reconfigure -phigh xserver-xorg
hope it helps

---

### Post by goodmaj on 2006-06-10
At the prompt type startx and then note what error messages you are receiving.  There is probably something peculiar about your display controller or you did something during the install indicated you did not want to proceed automatically to the desktop.

Post again with much more detail about error messages and what might be peculiar about your macine.

---

### Post by tnlogger on 2006-06-10
thanks  here is what I get after I log in 
( genecall@spare:$_) from what I have read it should log into the console with the blue screen.

---

### Post by ayoli on 2006-06-10
well it looks like you are in a console with a command prompt (ends with $) where you can type commands such as:
startx  #will startx or tell you what errors happened

sudo dpkg-reconfigure -phigh xserver-xorg # to reconf your x server if config is messed up

---

### Post by tnlogger on 2006-06-10
ok after running dpkg-reconfigure 
 I get the error xserver-xorg is not installed will I need to download Knome and install it from a disk. or is it in the system ? thanks

---

### Post by MKR. on 2006-06-10
Which CD did you download for the installation?

---

### Post by goodmaj on 2006-06-10
How did you do your install?  I would have expected the X configuration to have been taken care of during the install.

Did you do a Desktop install or a Server install?  What source are you using for the install? eg. LiveCD, Install CD etc.

---

### Post by tnlogger on 2006-06-10
I downloaded the new dapper install cd and installed the program on it on computer. as far as the install I went with the default install and and formated the whole HD in the install. I'll try a recovery and see if that helps . thanks

---

### Post by acorn22 on 2006-06-10
I am having the same problem. I used the alternate install cd since the computer I am using has low memory.

When I type startx it says command not found.

---

### Post by tnlogger on 2006-06-11
ok I did a complete reinstall and I get the error (failed to start the xserver. It is not set up correctly. Would you like to view the x swerver output to diagnose the problem)
 When I do I get this window ( X: cannot stat /ect/X11/X ( no such file or directory) ,aborting. )
 When I try to reconfigure It say no such command?

---

### Post by goodmaj on 2006-06-11
I am really not sure what is going wrong with your install, but based on the error you reported, it appears that /etc/X11/X does not exist.  It should be a link.  You can create the appropriate link with the following command.

sudo ln -s /usr/bin/Xorg /etc/X11/X

Then try startx agian and see what is reported.

---

### Post by goodmaj on 2006-06-11
Please read and folloow the suggestions in the following link:

[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

---

### Post by SilentNoise on 2006-06-11
I have the same problem and ur last command didn't make any difference. I still can't find xserver, or execute startx... :\

---

### Post by SilentNoise on 2006-06-11
Damn... I got the server version instead the desktop one...
tnlogger, check if u did the same... :D

---

### Post by mumushi on 2006-06-11
that answers it :D.

---

