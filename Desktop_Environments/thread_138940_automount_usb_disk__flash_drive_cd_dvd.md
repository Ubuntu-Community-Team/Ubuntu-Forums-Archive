---
title: "automount usb disk / flash drive cd dvd"
date: 2006-03-02
forum: Desktop Environments
---

### Post by rameshkumar on 2006-03-02
Dear Folks, 

I thought I should share a problem and it's solution, I had encountered with the automount feature in Breezy Badger.

Problem:
Immediately after a fresh installation of Breezy, I noticed automount was working well i.e. the icons for the relevant devices (flash drive/disk plugged into usb or if a cd/dvd was inserted into the CD/DVD drive) would appear on my desktop. After sometime (I suspected probably after an update of some packages etc.), I had lost all automounting capability. 
I could only mount the said devices manually, by enteringng something like 'pmount /dev/sda1' on a terminal, for example, to mount my usb flash drive.

Resolution:

I reinstalled the following 2 packages:

1. hal
2. hal-device-manager

Automount is now back in operation !  \\:D/ 

N.B. One might also want to re-install gnome-volume-manager, just to be sure.

Rgds.
Ramesh

---

