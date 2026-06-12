---
title: "Power button not working in Lubuntu"
date: 2010-09-25
forum: Desktop Environments
---

### Post by hesder on 2010-09-25
Hi,

Recently i've switched from ubuntu 8.04 to Lubuntu 10.04, since that time the powerbutton does not work anymore.

I've tried to find out how powermanagement is implemented in ubuntu to be able to debug this problem. But most documentation about this topic seems dated. 

I've already tried a few thing, most important stuff I did is: 
- tested the scripts in /etc/acpi/ and added a line to write something to a textfile when its called. But this file is not called when pressing the powerbutton.
- checked bios settings, seems alright (and these settings worked on 8.04 to).

Anyone suggestions?

Any references to more info about the proces that handles these events are helpfull to.

---

### Post by hesder on 2010-09-25
Just noticed in the menu "desktop sessions" the "power management deamon" was not checked. Seems simple enough and checked it, restarted system...

but no dice... power button still does nothing. There also is no way to set the powerbutton action from desktop gui. 

Writing this I noticed I forgot to check if the "power deamon" actually runs. Will check this tommorow.

---

### Post by hesder on 2010-09-27
The "power management deamon" is indeed running, but still does not call any of the ubuntu showdown scripts.

Any suggestions would be appreciated.

---

### Post by hesder on 2010-09-29
Update:

Visited [http://webchat.freenode.net/?channels=lubuntu](http://webchat.freenode.net/?channels=lubuntu), not a solution yet, but confirmed the powerbutton still works (using Xev).

It might be a problem with KMS. Will test this in the weekend by adding "nomodeset" to the end of the grub config file, to disable KMS when (re)booting.

---

