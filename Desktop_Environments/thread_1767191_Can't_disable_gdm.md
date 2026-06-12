---
title: "Can't disable gdm"
date: 2011-05-25
forum: Desktop Environments
---

### Post by szymi on 2011-05-25
Hi, 

I have Ubuntu 11.04 installed as a virtual machine on Virtual Box (in Windows). I need this system for testing every now and then, I'd like to keep it running in the background, but without GUI (I'd like to limit it's memory to just 256 MB). I've been trying to disable gdm the way I always used to do it in such situations:

```
$ sudo update-rc.d gdm disable 2 3 4 5
```But after reboot gdm auto starts again. Is this a bug or a new feature of 11.04? And if it's a feature, how can I disable gdm completely? 

Cheers,

Szymon

---

### Post by Krytarik on 2011-05-25
Please see this earlier post about that:
[http://ubuntuforums.org/showthread.php?p=10798400#post10798400](http://ubuntuforums.org/showthread.php?p=10798400#post10798400)

Greetings.

---

### Post by szymi on 2011-05-25
Nice one, thank you. That did the trick. So just to sum it all up in one place, to disable gdm in Ubuntu 11.04 I did: 

```
$ echo 'manual' | sudo tee -a /etc/init/gdm.override
```then I edited /etc/default/grub and set GRUB_CMDLINE_LINUX_DEFAULT to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```to disable graphical boot, and then last but not least I run

```
$ sudo update-grub
```to commit changes to /etc/default/grub.

---

### Post by sisco311 on 2011-05-25
Cool!

Don't forget to mark this thread as [SOLVED].

---

