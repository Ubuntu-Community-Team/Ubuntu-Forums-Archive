---
title: "Lenovo 3000 N200 fn brightness help"
date: 2010-08-01
forum: Desktop Environments
---

### Post by Casper Hansen on 2010-08-01
Hello,

I have Ubuntu 10.04 64-bit installed on my Lenovo 3000 N200 and almost everything works like a charm. Though I have one minor problem. I can't use the fn + F10/F11 to adjust the LCD brightness. I have to use the panel applet to adjust the brightness. 

Does anyone know how to fix this?

Regards,
C.

---

### Post by filiatra on 2010-08-06
Hello,

I have the same problem on Lenovo 3000 V200, and Ubuntu 10.04.
Applet works but fn+ F10, F11  doesn't.

Used to work OK on previous versions of Ubuntu..

thnx

ps. I saw on other threads that people solve this by using the command:

xrandr --output LVDS --set BACKLIGHT_CONTROL native

this returns to me:
warning: output LVDS not found; ignoring
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  24
  Current serial number in output stream:  24

---

### Post by filiatra on 2010-08-06
I solved this issue as follows:

$ sudo gedit /etc/default/grub

modified variable (added the word "nomodeset" in the end: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

then reboot.

If you do not have the file /etc/default/grub then you should first install grub2 as explained here:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Jas4cad on 2010-08-09
I am also running a Lenovo 300 N200, with 10.04 2.6.32-24
I have had no such problems with that. It works fine.
I am using the Nvidia graphics driver

How do you find you machine's fan behaviour ?

Jason

---

### Post by Casper Hansen on 2010-10-07
> **Jas4cad said:**
> I am also running a Lenovo 300 N200, with 10.04 2.6.32-24
I have had no such problems with that. It works fine.
I am using the Nvidia graphics driver

How do you find you machine's fan behaviour ?

Jason

Mine has an Intel onboard graphics. My fan is just fine.

---

### Post by Casper Hansen on 2010-10-07
> **filiatra said:**
> I solved this issue as follows:

$ sudo gedit /etc/default/grub

modified variable (added the word "nomodeset" in the end: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

then reboot.

If you do not have the file /etc/default/grub then you should first install grub2 as explained here:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Did no do the job. Do you have Intel graphics as well?

---

