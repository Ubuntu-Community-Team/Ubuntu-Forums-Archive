---
title: "Smartphone in VMWare (USB)"
date: 2007-11-03
forum: Desktop Environments
---

### Post by adonikam on 2007-11-03
I have a Cingular Smartphone 2125 running windows mobile 5.
I have a dell inspiron 8600 running ubuntu 7.10 (gutsy).
I have VMWare with Windows XP. 
What I want is to 
1) access the flash memory on the phone 
2) sync up my calendar/contacts.

When i was using 6.10, I was able to do both of these tasks using vmware/xp with activesync/outlook.

Since then I upgraded to 7.04, and shortly after 7.10. I had to run some stuff to get vmware to work in 7.10. So far this is my progress:

1) had no USB devices showing up under "USB Devices" on vmware. I ran "sudo mount -t usbfs /proc/bus/usb" and put it in the fstab file.
2) USB devices now showed up (my bluetooth stick and my phone).
3) I went into vmware, and the phone wasn't appearing. so I went into the device manager, and the phone was listed under "Network Adapters" and had a big fat exclamation point. I tried a lot of driver install stuff, and fiddled, but couldn't get it to work.
4) i removed all the drivers for USB devices (flash disks, phone stuff) but not the controllers. 
5) when i "rebooted", now the phone doesn't even appear on the list of "USB devices" anymore in vmware. the bluetooth does, but the usb doesn't.

So, I guess there are many theoretical ways to get access to my phone, but i haven't been able to get any to work (bluetooth included, and native ubuntu support). 

So, anyone know how  i can get my phone to appear on the list again as a usb device?:)

---

### Post by pronto185 on 2007-11-03
I have a HTC wizard (the 8125 from cingular), and to get access to my SD card on the phone i use a program WM5torage
[http://www.freewareppc.com/communication/wm5torage.shtml](http://www.freewareppc.com/communication/wm5torage.shtml)
it makes the phone act like a usb thumb drive, so you can easily add/remove files

but for the calendar/contacts not sure how to do that, my only suggestion there would be to try wine...

---

