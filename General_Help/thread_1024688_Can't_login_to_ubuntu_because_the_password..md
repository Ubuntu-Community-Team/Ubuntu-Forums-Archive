---
title: "Can't login to ubuntu because the password."
date: 2008-12-29
forum: General Help
---

### Post by Bensal1992 on 2008-12-29
Hello,
I installed Linux Ubuntu 8.10 64 bit and I add the HEBREW language to keyboard layout and now I can't write in English.
I tried to do all possible options like alt+alt and some thing in the Terminal (through the Live CD).

*I have dual boot (vista and ubuntu)

Thank!

---

### Post by Therion on 2008-12-29
Okay, never heard of this issue before, but you could try going to System/Preferences/Keyboard and then clicking on the "Layouts" tab and then on the "Reset to Defaults" button and see where that gets you. 

Good luck!

---

### Post by eBoxNet on 2008-12-29
Boot up from live cd.
open up a terminal window and type ```
gksudo gedit /etc/X11/xorg.conf
```

Locate ```
 Option "XkbLayout" "WHATEVER"
``` and replace with ```
 Option "XkbLayout" "us"
```

hope this will solve your prob,i never saw this before but i think it may work

---

### Post by eBoxNet on 2008-12-29
Sorry i gave you a url for code lol (i think i am tired)
i edited the post its fine now.

---

### Post by Bensal1992 on 2008-12-29
> **eBoxNet said:**
> Boot up from live cd.
open up a terminal window and type ```
gksudo gedit /etc/X11/xorg.conf
```

Locate ```
 Option "XkbLayout" "WHATEVER"
``` and replace with ```
 Option "XkbLayout" "us"
```

hope this will solve your prob,i never saw this before but i think it may work

I Entered to live cd and open the terminal and I wrote the command that you gave me. some window open to me and then I wrote "Option "XkbLayout" "heb" and this line mark yellow I replaced that with the "us" and I going to save : 
[IMG]http://img81.imageshack.us/img81/237/xorgea0.png[/IMG]

---

### Post by eBoxNet on 2008-12-29
my bad,you have to mount your disk first in order to edit this file via live cd,

try this :

1.```
sudo mount /dev/sda1/mnt
```
2.```
sudo nano /mnt/etc/X11/xorg.conf
```

"the file shouldn't be empty" we don't need to create a new one we just need to edit it.

in order to save your file hit CTRL+O (this is not a zero)

---

### Post by Bensal1992 on 2008-12-29
> **eBoxNet said:**
> my bad,you have to mount your disk first in order to edit this file via live cd,

try this :

1.```
sudo mount /dev/sda1/mnt
```
2.```
sudo nano /mnt/etc/X11/xorg.conf
```

"the file shouldn't be empty" we don't need to create a new one we just need to edit it.

in order to save your file hit CTRL+O (this is not a zero)

What I need to do here?:

[IMG]http://img187.imageshack.us/img187/2070/screenshot1og3.png[/IMG]

---

### Post by eBoxNet on 2008-12-29
ok propably your disk didn't get mount properly,so hit alt+f2 anf type ```
gksudo nautilus
``` wait a few secs and then in the new window click your hdd (the one with ubuntu installed) and navigate to /etc/X11/ then locate the xorg.conf and open it with text editor..if you manage to open the file then adit it and save it,reboot your pc from hard disk.

---

### Post by hyperdude111 on 2008-12-29
I cant remember where but i recentley saw a thread in the "howto" section explaining how to bypass the password check in ubuntu, i will look for it and if i find it i will link to it here.

---

### Post by eBoxNet on 2008-12-29
by booting up on repair mode...you can do this 2 boot up on repair mode and edit the file

---

### Post by Bensal1992 on 2008-12-29
> **eBoxNet said:**
> by booting up on repair mode...you can do this 2 boot up on repair mode and edit the file

How exactly I can do that?

---

### Post by eBoxNet on 2008-12-29
did you try ALT+CTRL+F1 while on login screen?
if you wanna boot ubuntu on recovery mode just choose recovery mode on your boot loader screen (grub)

---

### Post by judydogan on 2008-12-30
heres one better....i cant logon because of username and password     i fell asleep while it was installing and it went ahead without me  . i have no clue what to do....My first time using linux 
thanks for any help at all in advance

Judy

---

