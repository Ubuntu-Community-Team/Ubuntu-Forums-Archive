---
title: "Boot exchange between windows and ubuntu"
date: 2011-08-27
forum: Desktop Environments
---

### Post by gabala on 2011-08-27
This is my case:

I connect remotely to my PC in the lab in the university. It runs both Ubuntu and Windows 7.  I need to switch between windows and linux. However, since I am running applications under university license I can not use one of them as virtual machine.

To change between the two system, I can think of two possible solution but do not know how it is possible to do.

One is before restarting computer, set up boot loader to boot other OS only once and the next time come back to default OS. 

The second way is to be able to control boot loader options from both operating systems. Therefore every time before restarting the computer I select the other OS as default selection and restart the computer.

I do not know which of these ways are practically possible to do and if it is possible how should I do that!?

I am open to other methods to solve this problem. The current boot loader is windows'.

Thanks.

---

### Post by drawkcab on 2011-08-27
It sounds like you need a second computer.

---

### Post by Krytarik on 2011-08-27
> **drawkcab said:**
> It sounds like you need a second computer.
Very funny! ;-) No, seriously, please have a look at this earlier thread, maybe my reply is finally of help for someone:

[http://ubuntuforums.org/showthread.php?t=1633262](http://ubuntuforums.org/showthread.php?t=1633262)

Obviously, you need to install Grub2 as the boot loader therefore. For this, and more, this guide might be of help:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Greetings.

---

