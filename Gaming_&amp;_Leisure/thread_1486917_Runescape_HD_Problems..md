---
title: "Runescape HD Problems."
date: 2010-05-18
forum: Gaming &amp; Leisure
---

### Post by Kidfork on 2010-05-18
Alright so I've never had a problem with RuneScape in Windows 7. MY problem is in Ubuntu 10.04 when I load up the game I cannot load into OPENGL mode or SOFTWARE mode. This limits me from accessing High Detail. I'm Stuck on "safe mode" and cant go about minimum. 

Computer Specs in Signature

---

### Post by Kidfork on 2010-05-19
bump

---

### Post by TheStroj on 2010-05-19
Runescape runs perfect for me, I never had any problems with it.
Since its the graphics problem, maybe it is something wrong with drivers? Or no drivers at all?
If not, you can also try other browsers (lets say you use firefox) like Chrome, Opera...

---

### Post by Kidfork on 2010-05-19
tyler@tyler-laptop:~$ glxinfo | grep -i renderer 
OpenGL [COLOR="DarkRed"]renderer[/COLOR] string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2

---

### Post by Kidfork on 2010-05-19
tyler@tyler-laptop:~$ glxinfo | grep -i renderer 
OpenGL[COLOR="DarkRed"] renderer[/COLOR] string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2

---

### Post by Kidfork on 2010-05-19
bump

---

### Post by alex1996arm on 2010-05-19
Have you tried installing the proprietary drivers for full hardware acceleration?
If not,to install the drivers,go System -> Administration -> Hardware Drivers

---

### Post by Kidfork on 2010-05-20
> **alex1996arm said:**
> Have you tried installing the proprietary drivers for full hardware acceleration?
If not,to install the drivers,go System -> Administration -> Hardware Drivers

Thanks For the Reply, sorry to say but the chip doesn't show up in the "HardWare Drivers" tab. Only my wireless chip does.

---

### Post by alex1996arm on 2010-05-20
you running 64 bit?

---

### Post by apoorvumang on 2010-05-29
I am having EXACTLY the same problem. Plus, I have the same integrated graphics card as well. Any help will be appreciated!

---

### Post by Nighcraw1er on 2010-05-29
Are you trying to play the game via Firefox or the Runescape Windows Client? It may be that your Display Drivers are not installed. Try updating them to the latest recommended by Ubuntu.

---

### Post by bizhat on 2010-06-11
I am having the same problem with Ubuntu 10.04. This ubuntu is installed today. Some days back, i have installed Ubuntu 10.04 from same CD on same computer (was trying Win7), runescape used to work perfectly.

So i doubt, it may be caused by latest RS upgrade. It worked perfectly in Win 7 and Win 2003 (i tested both today).

---

### Post by Triggerhapp on 2010-06-12
[http://www.phoronix.com/scan.php?page=news_item&px=ODIwMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODIwMQ)

This is your answer. Linux simply does not have good enough Intel 3D acceleration, it's not the fault of your card (as you said, works in Windows)

Standard mode is currently Windows only, as is DirectX (obviously), so until Intel upgrades the 3D ability of their driver, Safe mode is your only option.

I feel your pain too, I currently have only 1 non-Intel machine.

---

