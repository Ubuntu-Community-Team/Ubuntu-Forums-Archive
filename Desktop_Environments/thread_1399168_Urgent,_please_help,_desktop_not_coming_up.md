---
title: "Urgent, please help, desktop not coming up"
date: 2010-02-05
forum: Desktop Environments
---

### Post by alex_foreman on 2010-02-05
hi guys,

im quite new to ubuntu so sorry if this is rather nooby,
i just updated ubuntu and it is no longer loading up to the login screen instead it is loading up a black command line screen i have tryed startx but that has done nothing, any ideas?!

it loads to gnu-grub

---

### Post by Leppie on 2010-02-05
try the command "set" (without the quotes) and post the output.

---

### Post by alex_foreman on 2010-02-05
the reply i got was
 
?=1
color_highlight=
colour_normal=
loop=loop0
pager=
prefix=(hd0,3)/boot/grub
root=loop0
show_panic_message=false

---

### Post by Leppie on 2010-02-05
is this a wubi install?

---

### Post by alex_foreman on 2010-02-05
yes it was, i installed it a while ago and it worked fine, its just after the update if had the problem though.

---

### Post by Leppie on 2010-02-05
try the following:
```
set root=(loop0)
linux /boot/vmlinuz root=/dev/sda1  loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img
boot
```if it takes you into ubuntu, then run the following command:
```
sudo update-grub
```

---

### Post by alex_foreman on 2010-02-05
when i rn the second command it says not disk found,
and if i run the command boot it says no kernal loaded

---

### Post by Leppie on 2010-02-05
do you happen to have an ubuntu livecd at hand (or can you download and burn one)?
i would need to know on which partition windows is installed.

---

### Post by alex_foreman on 2010-02-05
i dont no, however i beleive windows and ubuntu are installed on the same partition, when i load up my computer on windows it donst have any other partitions other then the c:drive

---

### Post by Leppie on 2010-02-05
well, then try the same commands but change the number 1. try first with 2, if the command gives an error try the same command but replacing the 2 with 3:
```
set root=(loop0)
linux /boot/vmlinuz root=/dev/sda[COLOR=Red]2[/COLOR]  loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img
boot
```

---

### Post by alex_foreman on 2010-02-05
sorry, tryed that and it said file not found

---

### Post by Leppie on 2010-02-05
and like this:
```
set root=(loop0)
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1  loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot
```

---

### Post by andrewdvalles3 on 2010-02-05
I am having the same issues.  Following the command structure recommended, I wound up with BusyBox.  Any suggestions?

---

### Post by alex_foreman on 2010-02-05
i got no error msgs that time, however it came uo with a load of wrighting and then it went to a solid black screen

---

### Post by alex_foreman on 2010-02-05
jst restarted and tryed it again and its now saying error: no such disk

---

### Post by alex_foreman on 2010-02-05
wait, i had typed it wrong, i to know have the busybox

---

### Post by alex_foreman on 2010-02-05
just saw before it goes into the busy box, it says
alert  /host/ubuntu/disks/root.disk does not exist. dropping to a shell

however i have checked the files on my windows boot and the file is in

c/ubuntu/disks/root.disk

---

### Post by Leppie on 2010-02-05
well, if it drops you to a shell (ubuntu shell) we can work from there.
issue the following command and post the output:
```
sudo fdisk -l
```

---

### Post by alex_foreman on 2010-02-06
i tryed that and it says
sudo not found,

i dont think it is an ubuntu shell, it says built in shell or something along those lines

---

### Post by itsme33 on 2010-02-06
try the recovery mode....dude

---

### Post by alex_foreman on 2010-02-06
... how do i do that, im new to ubuntu so dont know how to do much. instructions would be great!

---

### Post by Leppie on 2010-02-06
to boot into the recovery console:
```
set root=(loop0)
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2  loop=/ubuntu/disks/root.disk ro **[COLOR=Red]s[/COLOR]**
initrd /boot/initrd.img-2.6.31-14-generic
boot
```mind the final "s" in line 2

---

### Post by alex_foreman on 2010-02-06
when i do that, i still get the  error, /hosts/ubuntu/disks/root.disk does not exist, i have checked on windows and it is there in my c drive!!!

i dont understand why it wont find it :S

---

### Post by Leppie on 2010-02-06
in [post #14]("http://ubuntuforums.org/showpost.php?p=8780296&postcount=14") you said that you got a screen with a lot of writing, what did you do exactly to get there?

do you have any important information stored in your ubuntu installation?

---

### Post by faical117 on 2010-02-06
try Ctrl+Alt+F7

---

### Post by alex_foreman on 2010-02-06
dw guys, i am doing a reinstall of it, i dunno what the hell happened lol, thanks alot for all your help though!!

---

### Post by Leppie on 2010-02-06
> **alex_foreman said:**
> dw guys, i am doing a reinstall of it, i dunno what the hell happened lol, thanks alot for all your help though!!
if you really are interested in ubuntu, you may want to try a side by side install. it really is not so very difficult. if you want some help with that, let me know.

---

### Post by alex_foreman on 2010-02-06
how do you do that, that would be sweet if u could link me to a guide or tell me urself!!!

---

### Post by Leppie on 2010-02-06
from your windows installation:
- go to the control panel and open the "Add/remove programs" applet (i forgot what it's called in French, i'm sorry)
- select the ubuntu/wubi install and uninstall
- create any backup if you fear data loss (creating backups will never really hurt, it will only take up free space on harddrives).

make sure that you have disk space available for the new installation:
- in the control panel, go to "Administrative tools"
- select "Computer Management"
- go to the disk management section
- select your hard drive
- make sure there is free space, if not shrink a partition so there is at least about 30gb free. if you are unsure about the partition table, post a screenshot of the disk management showing your harddrive.
- apply new settings if changes were made.

reboot the computer an boot off the ubuntu livecd:
- after having chosen your preferred language, select to install ubuntu
- follow the instructions up till the partitioning part
- choose to have ubuntu use the largest contingent free available space to install into
- follow the instructions to set up the primary user account
- set up account copy from windows if desired
- activate the installation

this is just an outline. if you need more specific information, just let me know what else you need to know.

---

### Post by M&amp;StL on 2010-02-07
I have been following all of this facing the same problem. I am still stuck. My 64 bit notebook pulled the same no load after doing an update a few hours ago. The dark side, MS, is uneffected.

23:15 here. Will check tomorrow for any ideas. 
My knowledge of programming is zilch.

---

### Post by TriadHonor on 2010-02-07
This is a well knowed bug of Wubi, and about all installations can suffer it.

I just post a guide on how to solve it from Windows, read it and tell me if it works like for me.

The discussion is here ---> [http://ubuntuforums.org/showthread.php?t=1400608](http://ubuntuforums.org/showthread.php?t=1400608)

---

