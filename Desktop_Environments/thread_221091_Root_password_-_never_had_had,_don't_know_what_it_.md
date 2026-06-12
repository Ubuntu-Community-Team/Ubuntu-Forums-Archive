---
title: "Root password - never had had, don't know what it is....."
date: 2006-07-22
forum: Desktop Environments
---

### Post by johnvand on 2006-07-22
Having never setup Linux before I may have overlooked or simply not paid attention to the root password.  I need root privileges to install a printer and I cannot get into root.  I only ever use 3 different passwords and not one of them works.

Does Ubuntu set a default password, if so, what is it and, if not, how do I find out what it is?

Your answers would be greatly appreciated.

Thanks in advance,

John

---

### Post by reacocard on 2006-07-22
ubuntu uses sudo instead. the root account is disabled by defailt. more info on sudo and root can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ziox on 2006-07-22
by default, ubuntu locks the root account, instead you can use "sudo" which allows full access to the system.

for the graphic equivilant of sudo is gksu...

when either of them prompts for a password, it is usually asking you your own password...

now from what method/s are you adding printer? 

System => Admin?
or command line?

---

### Post by taurus on 2006-07-22
In Ubuntu, root account is locked on default so there is no password to it.  If you need to access your system as root to install something, use the sudo command instead, i.e.,

```

sudo <command name>
(then enter the same password that you use to log in...)

```

---

### Post by Amaranth on 2006-07-22
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically, the root account is disabled. Instead of logging in as root you run commands with sudo like this:```
sudo apt-get update
```

If a dialog popups up on your desktop asking for an administrator password it wants your password.

---

### Post by johnvand on 2006-07-22
Thanks a bunch guys - can you tell I'm a newbie (or even worse, an XP user !!) ?

John

---

### Post by taurus on 2006-07-22
> **johnvand said:**
> Thanks a bunch guys - can you tell I'm a newbie (or even worse, an XP user !!) ?

John
And hopefully, you won't go back to that OS again!!!  ;)

---

### Post by -deadcats on 2006-07-22
> **johnvand said:**
> Thanks a bunch guys - can you tell I'm a newbie (or even worse, an XP user !!) ?

Everybody gets here from somewhere. 

Welcome! :)

-dc

---

### Post by johnvand on 2006-07-22
I have downloaded the install file from Samsung.  When uncompressed there is an autorun command - from there I am supposed to be prompted - doesn't work !!

---

### Post by Ziox on 2006-07-22
what file did you download? it is best to download a .deb file if there is one.

---

### Post by taurus on 2006-07-22
Autorun is for Windows crap and it's not going to run in Linux without any kind of emulator!  What are you trying to install anyway?

---

### Post by johnvand on 2006-07-22
There was no choice - Samsung provides only one file - which I unzipped.  When I go to that directory the autorun file I'm supposed to execute is there but "sudo autorun"  does nothing - I get a command not found.

---

### Post by taurus on 2006-07-22
Again, what are you trying to install from Samsung?  :confused:

---

### Post by Ziox on 2006-07-22
you can use windows files in linux, that includes .exe, .dll, .msi files...

---

### Post by johnvand on 2006-07-22
A CLP500N colour laser printer - they provide an alleged Linux driver - so far it's vapourware ;-)

---

### Post by Ziox on 2006-07-22
> **johnvand said:**
> A CLP500N colour laser printer - they provide an alleged Linux driver - so far it's vapourware ;-)

have you tried to install the driver via System => Admin => Printing?

---

### Post by taurus on 2006-07-22
Why don't you configure your Samsung color printer from the menu and see if your model is on the list!  If it is, then it's as easy as walk in a park.  Otherwise, you need to download a linux driver for it...

---

### Post by johnvand on 2006-07-22
It's not on the list which is why I'm trying this method.

---

### Post by Franks&amp;Beans on 2006-07-23
I am installing a Samsung 4216F Laser Multifunction Printer as well trying to use the Samsung Linux driver.

To install, change to the cdroot folder created after taring the download file:

sudo ./autorun

this should work.

This seems to install a configuration program. I then went to the system printer wizard and found that the printer was now listed. I installed it there and thats it - comes up with the new printer icon - Ready.

Only problem - damn thing doesn't print?????

When I try to install the driver in the wizard it seems to ask for a PPD file - what is this?

---

### Post by johnvand on 2006-07-24
Tried tht too - doesn't see the "autorun" file - bummer.

Anyway, thanks for the help - if I find a solution I will post.

---

