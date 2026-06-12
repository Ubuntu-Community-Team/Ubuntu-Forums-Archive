---
title: "Logitech QuickCam communicate STX"
date: 2006-01-08
forum: Desktop Environments
---

### Post by rado_london on 2006-01-08
Hi
Yesterday I bought a webcam- Logitech QuickCam  Communicate STX. I was looking around google for a howto set it up but i didnt found anything. The interesting thing is that som of the sites say thst it is supported by linux.

My question is: How to get it running under linux. I tried camorama but the computer blocks completely.

PS Im not that advanced so if it is possible the guide to be easier.

Thanks in advance

---

### Post by Ampersand on 2006-01-08
It might be worth trying it with xawtv or camstream, I've found that some programs are better than others at finding cameras. Also, try installing usbview, this should tell you whether it's being recognised or not.

---

### Post by rado_london on 2006-01-08
Thanks but can u give me more info about how to install them and how to use them.

Thanks in advance

---

### Post by rado_london on 2006-01-08
Hey I tried camstream. It recognises my webcam but when I click to preview it the computer blocks,i cant move the mouse , cant use CTR+ALT+BACKSPACE or CTRL+ALT+F1. I need to make hard restart. The same thing happens when I try to run camorama. But its a fact that camstream recognise my webcam. I dont know why it crash my system.

DO u have any ideas?

---

### Post by SuperCzar on 2006-01-08
this is a problem with breezy.... i cant use my webcam either, there were work arounds, but last i heard they arent working anymore.

The devs say that its fixed in Dapper, but there are no plans to patch the breezy kernel to implement this fix.

here's a thread about it.
[http://www.ubuntuforums.org/showthread.php?t=70657&page=3](http://www.ubuntuforums.org/showthread.php?t=70657&page=3)
the link goes straight to arnieboy's fix... which doesnt work for me and others anymore.

---

### Post by rado_london on 2006-01-08
I just tried it everything went ok but when i started camstream the same crash happend.
Do you know if this is fixed in the Dapper Flight CD 2?

---

### Post by SuperCzar on 2006-01-08
there's a link to the bugzilla report in that thread somewhere, and apparently its fixed now in dapper, so i can only assume that its going to carry over to the flight cd2

---

### Post by rado_london on 2006-01-08
Tommorow I will take the risk of installing the flicht cd and I will post the results.

Wish me good luck!

EDIT: I just want to know do I need to install the same things in Dapper or it shout work out-of-the-box?

---

### Post by chele on 2006-01-14
EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") is a cool utility to update, download and build drivers for many webcams.

---

### Post by rado_london on 2006-01-19
Hi folks

I have great news!!!

I have tested my LogiTech Communicate STX using Dapper Flight 3 LIve CD and it works out of the box using eitheer gnomemeeting or camorama.
The quality still isnt as good as the one in windows but hopefully it will be improved.:D :D :D

---

### Post by dolson on 2006-02-27
I have a Logitech Communicate, but I don't know if it's STX or not.. I don't have the box or anything, just the cam itself. I plugged it in, and it does not work.

Could you tell me the output of `lsusb` for your cam?

---

### Post by rado_london on 2006-03-19
```
rado@linux:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 046d:08ad Logitech, Inc.
Bus 001 Device 004: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 001 Device 001: ID 0000:0000

```

---

### Post by timas on 2006-03-19
For references.. I don't have a QuickCam communicate, but perhaps it shares some extra light..

$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c509 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 006: ID 046d:08b4 Logitech, Inc. QuickCam Zoom
Bus 003 Device 004: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB Flash Drive
Bus 003 Device 003: ID 04cc:1122 Philips Semiconductors Hub
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I'm having trouble getting kopete to work with my cam.. it crashes as soon as I attempt to open the 'devices' item in the configure menu

---

### Post by rado_london on 2006-03-19
I have a question.
I use my webcam under breezy but the video quality is times worse than the same camera in Windows. When we will finally get the opportunity for using 100% support for peripherals.

---

### Post by dolson on 2006-03-19
That's a question you have to ask Logitech...

---

### Post by rado_london on 2006-03-20
They are cu*ts. ANd actualy most of the hardware and peripheral companies. It is so easy to make drivers. And they will benefit.

---

