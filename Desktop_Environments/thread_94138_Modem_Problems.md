---
title: "Modem Problems"
date: 2005-11-23
forum: Desktop Environments
---

### Post by Don M on 2005-11-23
Hi
   I am new to ubuntu linux and I can not figure out how to get 5.10 to recognise my modem and set up a dialer to get on line?
  I have a duel boot system also running Win XP. My Modem is a USRobotics Performance Pro model 5610B
  any help would be appreciated.
   Don M

---

### Post by paddyg on 2005-11-23
if it's a PCI modem, it's a winmodem and it usually needs windows to work.
You'll have a hard job to make it work here. Life would be easier if you had an external (serial) modem...

---

### Post by Don M on 2005-11-24
paddyg
   My USRobitics 56K Performance Pro Modem that will work with windows and with Linux kernel 2.3 and higher.
  thanks for any help
  Don M

---

### Post by az on 2005-11-24
[QUOTE=Don M]paddyg
   My USRobitics 56K Performance Pro Modem that will work with windows and with Linux kernel 2.3 and higher.
  thanks for any help
  Don M[/QUOTE]

When you boot, does it say that alsa is configuring more than one device?  If so, then your modem is set up my alsa as /dev/ttyS14.  Try entering that to set up your modem when asked for the device.

---

### Post by towsonu2003 on 2005-11-25
first, sudo apt-get wvdial

sudo wvdialconf /etc/wvdial.conf

if it says it saw your modem, you'll know where it is :) (and you're lucky)

u can use it to dial ( read man wvdial , almost simple)

if not:

try going to linmodems.org (with another computer :) ), read the stuff they wrote, download scanModem tool, read its readme, run, and decipher its output (which might tell you whether you have a winmodem). if following instructions dont work, you can email their mailing list... 

good luck...

---

