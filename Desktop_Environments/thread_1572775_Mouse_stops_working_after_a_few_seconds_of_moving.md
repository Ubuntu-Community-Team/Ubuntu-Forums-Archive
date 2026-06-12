---
title: "Mouse stops working after a few seconds of moving"
date: 2010-09-11
forum: Desktop Environments
---

### Post by Jerrac on 2010-09-11
Really odd problem that I have no clue how to troubleshoot. 

I boot up Ubuntu 10.04 just fine. The mouse works, but after about 2 seconds or so, it stops moving. Of course, the keyboard keeps working fine. It's like Ubuntu stops getting the signals that the mouse is moving.

The mouse is in fine working condition. It works fine on my Windows partition.

The mouse just had fresh batteries installed, and the laser light doesn't turn off. 

I did just remove an ATI card and go back to my GeForce 8200 onboard graphics card. So I thought it might be a wierd driver problem, so I managed to remove the NVIDIA drivers. Didn't help at all.

I also was able to log into a console and update the OS. No help there either.

I did try to boot my 10.04 live cd, but my computer hates live cd's for some reason. It wouldn't boot, and I can't remember what I did to make it work when I installed Ubuntu.

Any suggestions?

---

### Post by teilnehmer on 2010-09-12
I don't know much about mice, but do you see anything bad in dmesg? Try
```
dmesg | grep -i mouse
```
This will pull anything mousy from the messages.

---

### Post by optima4 on 2011-11-07
I know this thread is older but I am having such a hard time with Ubuntu that at this point I wish I had my crappy Windows 7 Starter back :( My mouse is not working the same way. Here is the report from that code
> 
[    1.347010] mousedev: PS/2 mouse device common for all mice
[    2.628657] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    2.629089] generic-usb 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.1-1/input0
[ 1139.897158] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input12
[ 1139.897879] generic-usb 0003:413C:3200.0002: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.1-1/input0

---

### Post by pavi_elex on 2011-11-08
Try this.
```
root@user-desktop:~# nano /etc/X11/xorg.conf
```
& add following code into file & save it.

```
Section "ServerFlags"
Option "AutoAddDevices" "false"
EndSection
```

---

### Post by janman74 on 2012-09-26
I have the same problem on my laptop. Trackpad works always great. My bluetooth mouse AND my wired mouse, both stop working for few seconds, sometimes for long time.

To register to this form was a real headache, thanks to my mice problem. Please help.



Using Ubuntu 12.04 LTS, 64-bit, both mice are Microsoft made.

---

