---
title: "Is there a device manager equivalent?"
date: 2009-06-03
forum: General Help
---

### Post by johnnyorourke on 2009-06-03
Hello, any help please?

Is there a device manager equivalent in Linux? I can't tell if Ubuntu is even seeing my firewire edirol fa-66 capture device. 

It seems to have auto-recognised my built in intel sound but for the life of me i can't suss how to get it to use my edirol, which is what i need for recording. 

I also have no idea how to update my graphics card driver. 

I thought I was fairly computer literate, but have only used windows for best part of 20 years. Is linux really more complicated to get set up? Or do i just need to tick the right boxes to get it to see my stuff. 

I have enabled firewire raw 1394 in ubuntu studio controls. I'm running ubuntu studio which has FFADO as standard and I've got everything updated. I'm using Hardy too, couldn't get jaunty to install. 32 bit intel too. 

many thanks,

Johnny

---

### Post by munky99999 on 2009-06-03
There are commands in the commandline that will do as such.

lspci is pci only hardware
lsusb is usb only hardware
lshw gives you info for all hardware.

hw will be long but you should be able to sift through it quickly enough. Easy and important one to remember.

As for gui lshw. Go into synaptic search lshw and get the gtk one.

---

### Post by maheshasolkar on 2009-06-03
How about the following:

[https://help.ubuntu.com/community/HardInfo](https://help.ubuntu.com/community/HardInfo)

[https://help.ubuntu.com/community/DeviceManager](https://help.ubuntu.com/community/DeviceManager)

---

### Post by johnnyorourke on 2009-06-03
Thank you both, I know have HAL Device manager which is exactly what  I was after. 

Turns out my edirol is seen but just not working yet. 

good news, ish.

---

### Post by Yellow Pasque on 2009-06-03
The nice thing about *sudo lshw* or *sudo lspci -vv* is it gives you information on the driver module being used.

Also, *dmidecode* gives a ton of info on a system.

---

### Post by shrinux on 2009-06-22
Thank you, maheshasolkar.
HardInfo is great one :)

---

