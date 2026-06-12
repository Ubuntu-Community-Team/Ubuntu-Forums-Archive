---
title: "power off the hd. And power on the Notebook."
date: 2007-10-08
forum: Desktop Environments
---

### Post by gaiterin on 2007-10-08
Hi.
How I can power off the internal hard disk of a notebook, without open physically?

I work with vibrations, and I think use sometimes a USB's linux (pendrive) for save more life of internal hard disk when I have vibrations in the environment. 

And how I can verify that it is really power off?

Thank you very much!
Marks.

---

### Post by gaiterin on 2007-10-09
I find hdparm.
It sleep the hard disk.

sudo umount /dev/hda
sudo hdparm -Y /dev/hda

My question is: Is the same sleep and power off? :O

Others solutions? Thanks!

---

### Post by gaiterin on 2007-10-17
The solution :)
Boot with Slax 6 ([www.slax.com](www.slax.com)).
in the directory /root/.kde/Autostart create a script shutdown.sh with the command:
hdparm -y /dev/sda
;)

---

