---
title: "dell studio one touchscreen with ubuntu?"
date: 2009-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by searayman on 2009-06-08
Does the dell studio one with touch screen work with Ubuntu. If I wipe vista and install with ubuntu will I be able to use the touch screen. If anyone has had any experience with this let me know. Also if you know of any youtube videos showign the studio one touchscreen with ubuntu also let me know.

---

### Post by yurtboy on 2009-08-13
any news on this?

---

### Post by Neodudeman on 2009-10-11
> **yurtboy said:**
> any news on this?

I've got the news! Check it, after probing one of the engineers, he gave me some useful info:

> 
It will work with single touch HID on Mac and Linux but not multi touch.
To make it work you may need to set the device to MAC mode in the USB Config application. 

This can be downloaded as part of the Touch+ suite. Go to the Mouse tab and switch on Enable Mac Compatibility.

Also  check out this web page for creating the driver for Linux: [http://www.nextwindow.com/nextwindow_support/app_working_under_linux_2.html](http://www.nextwindow.com/nextwindow_support/app_working_under_linux_2.html)


Here is the link for the USB Config application:
[http://www.nextwindow.com/assets/files/nwtouch28_inst.exe]("http://www.nextwindow.com/assets/files/nwtouch28_inst.exe")

According to the support site linked, in terms of drivers for Linux, the touchscreen can work with the [evtouch touch drivers]("http://www.conan.de/touchscreen/evtouch.html").

And here is the XF86Config-4:
```

Section "InputDevice"
     Identifier "touchscreen"
     Driver "evtouch"
     Option "Device" "/dev/input/event1"
     Option "DeviceName" "touchscreen"
     Option "MinX" "1"
     Option "MinY" "1"
     Option "MaxX" "32768"
     Option "MaxY" "32768"
     Option "ReportingMode" "Raw"
     Option "Emulate3Buttons" "false"
     Option "Emulate3Timeout" "50"
     Option "SendCoreEvents" "On"
EndSection

Section "ServerLayout"
     Identifier   "Default Layout"
     Screen       "Default Screen"
     InputDevice  "Generic Keyboard"
     InputDevice  "touchscreen"
     InputDevice  "PSAUX Mouse"
     InputDevice  "USB Mouse"
EndSection
```

I'm going to attempt these instructions, and I'll update on my success. (or failure)

---

### Post by Neodudeman on 2009-12-22
So, if anyone is curious, I've gotten the single touch half working.

The computer supports touch clicking, but the mouse does not move to where you touch.
I think it's cause the XORG modifications they gave us don't work for me. My X session just crashes when I try to put it in. I'm no expert either, so I'm not really sure what to do about it.

In any case,&#12288;ENAC Interactive Computing Laboratory has create multitouch software for linux:
[http://lii-enac.fr/en/projects/shareit/xorg.html](http://lii-enac.fr/en/projects/shareit/xorg.html)

They're still working on NextWindow, which is what the Dell Studio One uses.

I think I'm going to try fixing this a little more, but I'm going to be keeping an eye on that multitouch support.

---

### Post by Neodudeman on 2009-12-30
Good News! I got it working... somehow.

Not sure exactly what I did, but for some reason the touchscreen started working.

The most recent things I did was edit the xorg.conf and added a xorg touchscreen package.

Edited up the ServerLayout section, and to the InputDevice section, I changed
```
     Option "Device" "/dev/input/event1"
to	Option "Device" "/dev/input/by-id/usb-NextWindow_Touchscreen-event-mouse"
and added
	Option "CorePointer"
```

and added a dummy mouse input device, and put it into the server layout as well.
```

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection
```


```

Section "ServerLayout"
	Identifier "Main Layout"
	Screen	"Default Screen"
	InputDevice "touchscreen"
	InputDevice "dummy"
EndSection
```

And then did the following commands:
```

sudo modprobe usbtouchscreen
sudo apt-get install xserver-xorg-input-evtouch

```

and then, while I wasn't paying attention, it began working.

Maybe someone could try it and confirm these steps as fixes?

---

### Post by emoguitarist06 on 2010-01-13
> **Neodudeman said:**
> Good News! I got it working... somehow.
Maybe someone could try it and confirm these steps as fixes?

Anyone else got it working? I plan on purchasing a Dell Studio One 19 :)

---

### Post by ihuerta on 2010-01-15
I'm fighting my way with Dell Inspiron One Touch (I think it's the same model but with the spanish name). 

After some hours of trying, I wonder if anyone has the same Nextwindow Touchscreen model. lsusb reports:

```
Bus 002 Device 002: ID 1926:007a
```

Does anyone have the same USB ID?

---

### Post by HolySmoke86 on 2010-03-09
Hello everybody,

I recently ran into problems using this device (1926:007a) in xorg 1.7.5.901 (which is 1.7.6 RC 1) under Archlinux (kernel 2.6.32, i686) so I did some (web-) research:

The current version of xf86-input-evtouch (0.8.8) does neither build nor run  under xorg anymore because xf86GetMotionEvents was dropped from the  public API.
There is a [bug   report in launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313") concerning th[http://www.linuxquestions.org/questions/linux-hardware-18/touch-on-a-sony-all-in-one-vaio-770289/](http://www.linuxquestions.org/questions/linux-hardware-18/touch-on-a-sony-all-in-one-vaio-770289/)ese  devices and evdev, though a  solution is yet to be found.

The touch screen built into the Dell Studio One (or Dell Inspiron One)  is "1926:007a". According to [a post on linuxquestions.org]("http://www.linuxquestions.org/questions/linux-hardware-18/touch-on-a-sony-all-in-one-vaio-770289/") the ID of the NextWindow 1950 is "1926:0064", so the model in the Inspiron should be slightly higher. On that page there are also links to [an analysis of the ]("http://txzone.net/blog/index.php?post/2009/11/25/Hacking-the-Dell-SX2210T,-part-1.")[Dell SX2210T]("http://txzone.net/blog/index.php?post/2009/11/25/Hacking-the-Dell-SX2210T,-part-1."), which ships with said 1950 device.

Please do let me know if I can somehow help on getting this device to work. cause I won't be happy being stuck with Windows 7 on this nice piece of equipment ;)

Best regards, HolySmoke

---

### Post by ihuerta on 2010-03-09
Hi there!

I'm happy someone else has the same screen :). I finally managed to make it work with Ubuntu 9.10, thanks to a "prototype" driver NextWindow sent me.

Please take a look at the Launchpad bug where I just uploaded the instructions that worked for me: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313)  (comment 31).

---

### Post by HolySmoke86 on 2010-03-10
Hey ihuerta,

this does indeed work for me in Ubuntu 9.10 (my thanks to you). Is there possibly a mailing list one can subscribe to for information on recent progress of the driver?

---

### Post by ghost1347 on 2010-08-28
im new to linux wat do i do with the xorg.conf packet i downloaded [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG][IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]

---

### Post by redxine on 2010-09-05
Extract the xorg.conf file to your desktop by dragging it out of the archive manager. 

Open a terminal (Applications > Accessories > Terminal or Ctrl+Alt+T) and type:

cd Desktop
sudo cp xorg.conf /etc/X11/

it will ask for your [sudo] password. Type your password and press enter. Note that no asterisks (*) or characters of any kind are echoed back -- just keep typing.

Log out and log back in to apply the changes. Hope this helps, ghost1347.

---

### Post by Garryonapc on 2010-09-30
I bought a dell studio one last year. It never worked with windows, i was always slow and the CD drive did not work (despite changing it). After a while it just stopped working altogether and would not even boot.

I spoke to dell who were actually fine about it as it was still under warranty and purchased on a business account. They recently sent me a top of the range comp which has no problems. The funny thing was, they never picked up this rather new studio one.  So I did what I always do when I have a spare computer and some time, I installed Linux.

Using the latest Ubuntu (10.04) I have not had 1 single problem with it. including the CD drive and the touch screen, works fine.

Why did I ever need windows in the first place. 

Those of you who have a studio one and want the touch screen, just upgrade your Ubuntu to 10.04, easy!

---

### Post by COWBOY CAMILO on 2010-12-16
Hi U-All.. I recently bought the same PC Dell Studio one 19... first thing I did was install Ubuntu 10.10 pretty confident that the touchscreen was gonna work out of the box..... but I've tried everything and nothings seems to work...
Hope someone has the answer for this...
Cheers.

---

