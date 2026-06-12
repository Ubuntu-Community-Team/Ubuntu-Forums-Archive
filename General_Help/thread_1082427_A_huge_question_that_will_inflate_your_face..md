---
title: "A huge question that will inflate your face."
date: 2009-02-27
forum: General Help
---

### Post by noseforsharpies on 2009-02-27
How do I know if my PC is 32-bit or 64-bit? Likewise, how do I know if my current installation of Ubuntu is 32-bit or 64-bit?

THANKS! And for the Zeppelin-poppers.

---

### Post by howefield on 2009-02-27
Open a terminal, (applications > accessories > terminal) and type

```
uname -m
```

This will tell you what operating system you have, 32 or 64 bit.

Should be obvious how to interpret the output, but if not, post back here.

---

### Post by noseforsharpies on 2009-02-27
it says i686. not sure how to interpret that.

---

### Post by brokenLockpick on 2009-02-27
I often check the bios as a quick and dirty way to find out if the computer supports 64bit, generally there is a plain english entry that says if the cpu is 64 bit capable.

---

### Post by howefield on 2009-02-27
> **noseforsharpies said:**
> it says i686. not sure how to interpret that.

You have a 32 bit operating system, tell us what processor you have, and we can tell you if it supports 64 bit.

---

### Post by yther on 2009-02-27
He probably meant "uname -a"... which gives you information about the currently running kernel.  For instance, here's mine:

```
Linux hazuki 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 [COLOR="Red"]x86_64[/COLOR] GNU/Linux
```

Note the highlighted bit.  It will say 32 or 64 depending on what you are running.  *Edit:  Or possibly not.  It's been a while.  :(*

Now it's possible to run a 32-bit kernel on a 64-bit machine, but not the other way around.  Look at the file, /proc/cpuinfo for info on your actual processor.

---

### Post by noseforsharpies on 2009-02-27
AMD Turion 64 X2 Mobile Technology TL-60 
2.0 Ghz 512kb X2 L2 Cache

for the processor.

So how do I know what Ubuntu I have installed?

---

### Post by howefield on 2009-02-27
> **yther said:**
> He probably meant "uname -r"... 

No, he meant uname -m

---

### Post by brokenLockpick on 2009-02-27
> **noseforsharpies said:**
> AMD Turion [COLOR="Red"]64[/COLOR] X2 Mobile Technology TL-60 
2.0 Ghz 512kb X2 L2 Cache

for the processor.

So how do I know what Ubuntu I have installed?

indeed 64 bit capable

---

### Post by howefield on 2009-02-27
> **noseforsharpies said:**
> AMD Turion 64 X2 Mobile Technology TL-60 
2.0 Ghz 512kb X2 L2 Cache

for the processor.

So how do I know what Ubuntu I have installed?

You are running 32 bit Ubuntu, and your hardware supports 64 bit.

Your machine should be able to handle either 32 bit or 64 bit.

---

### Post by Yellow Pasque on 2009-02-27
```
uname -m
```
shows i686 for 32-bit and x86_64 for 64-bit

You have a 32-bit OS running on a 64-bit capable processor. I would not recommend reinstalling your OS just to run the 64-bit version unless you use your computer for tasks that significantly benefit from 64-bit (Photoshop, virtual OS's, math apps, video editing, etc.)

---

### Post by noseforsharpies on 2009-02-27
Thanks, guys. So I need to reinstall Ubuntu. One last question for the road: Do I need to make an Ubuntu-64 disk and reinstall it over this current installation? Do I perform that operation in the same way I did when I installed the 32-bit Ubuntu over *Vista*? Thanks.

---

### Post by brokenLockpick on 2009-02-27
> **Temüjin said:**
> ```
uname -m
```
shows i686 for 32-bit and x86_64 for 64-bit

You have a 32-bit OS running on a 64-bit capable processor. I would not recommend reinstalling your OS just to run the 64-bit version unless you use your computer for tasks that significantly benefit from 64-bit (Photoshop, virtual OS's, math apps, video editing, etc.)

I actually agree with this as far as not switching unless there is a good reason. I've had more problems with 64-bit versions than 32-bit versions. This may not be true overall but is personal experience. The other reason for switching to 64-bit is often due to the addressing limitations of 32 bit OSs when it comes to large amounts of RAM. In simple terms if you have 4ish GB or more you cannot utilize it all with a 32 bit OS.

---

### Post by ryan.nabinger on 2009-02-27
try 'dmesg | grep -i cpu' or 'cat /proc/cpuinfo' for cpu info

'uname -m' -- i686 is 32bit kernel.  64 should say x86_64 I believe

---

### Post by Yellow Pasque on 2009-02-27
> **noseforsharpies said:**
> Thanks, guys. So I need to reinstall Ubuntu. One last question for the road: Do I need to make an Ubuntu-64 disk and reinstall it over this current installation? Do I perform that operation in the same way I did when I installed the 32-bit Ubuntu over *Vista*? Thanks.
Yes, if you recently installed 32-bit Ubuntu and want to install 64-bit Ubuntu over it, burn the amd64 .iso and when the installer gets to the partitioning step, make sure you choose "Guided, use entire disk"

---

### Post by brokenLockpick on 2009-02-27
> **Temüjin said:**
> Yes, if you recently installed 32-bit Ubuntu and want to install 64-bit Ubuntu over it, burn the amd64 .iso and when the installer gets to the partitioning step, make sure you choose "Guided, use entire disk"

Do make sure to save any files you want to keep somewhere else like on a usb flash drive. You probably knew to do that but I've been surprised in the past by people saying "where did all my stuff go."

---

