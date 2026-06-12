---
title: "official way to create liveusb"
date: 2012-01-04
forum: Desktop Environments
---

### Post by z0rr099 on 2012-01-04
I'm new to Ubuntu, but not to Linux. I've spent 3 days trying various way to do what I'm trying to do without success. I've tried every method that anyone has suggested, but I still can't get it working. Here's what I'm trying to do;

I would like to install lubuntu (willing to work with ubunut if not possible with lubuntu) on a clean machine. I want to add/remove packages and my one custom program to the mix. I then want to remaster what I have already installed and put it on a usb stick so I can use it as a liveusb stick and have it boot on most computers. I want it working like a clean livecd, except on a usb stick, including the ability to detect hardware on the new or target machine.

I have tried remastersys, usb-creator, unetbootin, livecd-creator, etc. None seem to work with lubuntu 11.10. I've used a lot of these with other distros and they work just fine. I'm now trying with lubuntu and the best I've achieved so far is using remastersys, then unetbootin. However, when it tried to load, it comes up with an error about can't mount /dev/loop0 (/cdrom....). I'm NOT using a cdrom and want to boot from usb drive.

Is there an official document that explains how to do what I'm trying to do? I think I've read and tried everything in the ubuntu forums and am pulling what little hair I have left, out. ](*,)

---

### Post by spacecheck on 2012-01-04
How about trying these

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Spacecheck
(don't let it bounce)

---

### Post by Rodney9 on 2012-01-04
Also this - 

[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by z0rr099 on 2012-01-04
spacecheck, I tried all three of those suggestions. I couldn't get any of them to work.

Rodney9, tried what that thread suggested. Upon booting, it's looking for a cdrom and not a usb stick.

Here's a little more information. 

If I download the (or any version) lubuntu iso from ubuntu, I can use unetbootin to create a bootable usb stick. It works fine. 

What's different is that I want to create my own iso or image from my installed lubuntu that is already tweaked the way I want it. I've tried several methods, already mentioned, to try and create the iso file from the already installed version. I don't want the usb to have persistence capability. It should boot, properly detect hardware (graphics card, etc.) and boot the image (iso) that I've already created and put on the usb stick, just like a livecd. In other words, I want to create a liveusb from an already installed lubuntu instance. 

I believe that this is where my real problem lies. Whatever program I use, has to know how to create in image that can be booted from a usb drive and not from a cdrom. usb-creator-gtk says that it can do this, but all I get is a blank screen when I try the usb created from it.

Edit: This is the guide that I tried originally, but it's old and nothing seems to work with 11.10. It had a lot of links to other suggestions, which I tried. I really did spend 3 days trying to get this working. 

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I don't think my problem has to do with the usb stick or even getting the iso on it, but on creating an iso properly from a program that understands that I want the final, custom iso to boot from a usb stick instead of a cdrom. I'm trying to create a 'spin' or remaster lubuntu to create a liveusb version, not a livecd.

The links do work if I were creating a livecd. They just don't work if I'm creating a liveusb.

I'd like to hear from anyone that has successfully created a liveusb from any version of ubuntu. The tutorials either don't work for what I'm trying to do or I'm missing something important. I've created hundreds of livecd and liveusb sticks over the years with other distros. That's why I'm hitting my head against the wall on this one.

---

### Post by nepalnt21 on 2012-04-24
has anything come out of this? im interested as well

---

### Post by marinara on 2012-04-24
if it's not booting at all, it might be your pc hardware.  I have a PC from 2006 that won't boot from USB

---

### Post by RichardCain on 2012-04-24
-

---

### Post by techsupport on 2012-04-25
Use Remastersys like this:

[http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/](http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/)

It even shows you how exactly to use Startup Disc Creator, which is what you wanted to know would work.

I just tested it yesterday and it works perfectly for custom installations of Ubuntu.

Don't use dvd to install. Use USB Flash Drive Live Installation Sticks. Much faster that way too.

---

### Post by baberya on 2012-04-25
We used to watch it a lot when my eldest lad was younger and i could afford sky, some greats over the years, i used to like The Undertaker and his creepy sidekick Pall bearer
Thread merged etc. 
Àêòóàëüíûå [Âåêòîðíûå èçîáðàæåíèÿ](http://vectory.ru/) áåñïëàòíî 
[Âåêòîðíûé ðàñêðîé âûñå÷êà ïàïêè ](http://www.vectory.ru/index.php?productID=7280)  
[Magic Chef](http://www.vectory.ru/index.php?productID=9653)
 ðåãèñòðèðóéñÿ è ñêà÷èâàé

---

### Post by km3952 on 2012-04-25
You are looking to create a 'hybrid iso'; perhaps a search for that will get what you want.

---

