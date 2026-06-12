---
title: "Dell 1011 Netbook remix errors"
date: 2010-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gjensen1994 on 2010-08-22
Hi, I'm new to the Ubuntu forums, but I couldn't find a solution to this problem elsewhere so...

i am running a standard Dell 1011 with an XP/Ubuntu 10.04 netbook remix dual-boot and whenever I try to start up Ubuntu, I get a terminal-style screen saying

Ubuntu 10.04 LTS <computer name> ttyl
<computer name> login:

After I login, it pops up with this...

Last login <DATE>
Linux-2.6.32-21 generic #32-Ubuntu SMP Fri. Apr. 16 <time> UTC 2010 i686 GNU/Linux

Welcome to Ubuntu
documentation can be found at <URL>

0 packages can be updated
0 updates are security updates

run <command> statement

any help would be nice!

Thanks

---

### Post by mörgæs on 2010-08-23
Hvad sker der, hvis du skriver **startx**?

---

### Post by gjensen1994 on 2010-08-23
Alright, so when I type in StartX after I "login", I get that StartX was not found, so I tried to do sudo StartX, which after hitting enter says [sudo]password for <user>:  I then typed in the password and I got another error, so I tried root StartX, which then says the root is not currently installed, please type in sudo apt-pls intall root-system-bin, which I did and then it told me cannot find root-system-bin.

---

### Post by mörgæs on 2010-08-23
(Well, I thought you were Danish...)

It is not recommended to use a root user on Ubuntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Have you tried installing Ubuntu using this?
[http://ubuntuforums.org/showthread.php?t=1553467](http://ubuntuforums.org/showthread.php?t=1553467)

---

### Post by gjensen1994 on 2010-08-23
My family is from Denmark, yes, and I believe I did install it that way.

---

### Post by mörgæs on 2010-08-24
Did you write startx in small letters?

I think that we need something more on the background. Has the machine behaved like this from the installation, or is it a recent error? Did other versions work? Do you know which screen card it has? And so on - everything relevant.

---

### Post by gjensen1994 on 2010-08-27
No, I did not, i'll try.

This is my second install of ubuntu, the last one was causing problems because I used a third party software to re-partition the drive, then when ubuntu got installed, I lost 30 GB's, so I partitioned the 30 GB's and it no longer worked because of the partition difference.

---

