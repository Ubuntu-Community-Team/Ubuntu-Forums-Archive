---
title: "need help changing GRUB defaults"
date: 2005-12-17
forum: Desktop Environments
---

### Post by mjshepherd on 2005-12-17
Hello Ubunteros,

I am new to the Ubuntu OS, having loaded it onto my secondary (slave) hard drive, to see what it can do. However i also want to run Windows 98 SE as well from my main (master) hard disk.  I have successfully installed GRUB boot-up facility to enable switching between the two systems.  However, every time my wife turns on the computer to get to windows, she has to leave the computer to save our baby from throwing herself downstairs, and the GRUB system defaults to Ubuntu - which she does not want - yet!

Is it possible to change GRUB so that Windows is the default OS, and if so, how?  I've had a quick look at editing the commands it uses, and i haven't a clue what to do!

Cheers

Matthew

---

### Post by aysiu on 2005-12-17
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` You'll see a line that says *default 0* Change it to something else.

Numbering starts at 0 (not 1), so my guess is that you probably having a numbering scheme like this:
0 Ubuntu
1 Ubuntu recovery mode
2 Ubuntu memtest
3 Other operating systems
4 Windows

If so, change it to *default 4* and save.

---

### Post by mjshepherd on 2005-12-17
Sorry Aysiu,  but where do I type this in?  I tried it having pressed "c" during GRUB boot up to get a command line, and typed in your code, but got nothing but error messages. Do I have to type in "sudo" and the spaces too? And on the same number of lines as you used in your example.  Sorry for my ignorance of this...

Thanks,  Matthew

---

### Post by tuxy on 2005-12-17
First you have to open a command console. Edit the /boot/grub/menu.list as "root". 
Before you do this back up the /menu.list file. In case if you stuff it up you have a backup copy.

You can edit the file by any text editor. There is an option 'default 0' change it to 4 or whatever series your Windows 98 comes in. Just have a look at the /menu.list file contents you will get an idea what it is.

You can also change the default time out(which is 10secs) to whatever amount of time you want.

---

### Post by aysiu on 2005-12-17
[QUOTE=mjshepherd]Sorry Aysiu,  but where do I type this in?  I tried it having pressed "c" during GRUB boot up to get a command line, and typed in your code, but got nothing but error messages. Do I have to type in "sudo" and the spaces too? And on the same number of lines as you used in your example.  Sorry for my ignorance of this...

Thanks,  Matthew[/QUOTE] Whoops. Sorry. Sometimes I assume too much. Sometimes I assume too little.

You don't edit it during the Grub boot-up. You boot up. Go into Ubuntu. When you get there, click on Applications > Accessories > Terminal.

A DOS-like command prompt will pop up. That's where you enter the commands. Just copy and paste them from my previous post.

---

### Post by mjshepherd on 2005-12-18
Thanks, Aysiu,

I've tried this and now it works beautifully.  Don't worry about your assumptions, i'm sure i know very much less than the average ubuntero!

Cheers

Matthew

---

