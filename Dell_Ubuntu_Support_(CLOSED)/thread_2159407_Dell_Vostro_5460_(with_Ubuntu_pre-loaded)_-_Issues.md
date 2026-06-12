---
title: "Dell Vostro 5460 (with Ubuntu pre-loaded) - Issues"
date: 2013-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by purezen on 2013-07-03
Hey guys !

I bought a Dell Vostro 5460 (Model No: W560303TH - Thailand version) a month back. It is equipped with i5-3230M and nVidia 630M (2 GB).
It came pre-loaded with Ubuntu 12.04 and from what I could gather there were a fair amount of customizations done to the installation. From what I could see, there were some kernel modules and even a Dell repository added as a software source.

BTW, this is the first time that I am using a laptop with a Linux distro pre-installed.

Also, I soon did a fresh install of Ubuntu 12.10 x64 since I am already a fairly old Ubuntu user.
And these are the issues that I am probably facing due to the OS (with the OEM installation as well):

**Sound:**
This is the most important issue with the laptop. The  sound output is only feeble although from what I could gather, the users  of the Windows version are not facing any such issues.

**Ethernet:**
This is a one more crucial issue that I am facing. The  ethernet port is not detected by the OS. Though, when I connect the 5460  to my router via a cable, the ethernet LED lights up on the router.  However, there is no activiy in my OS. Also, there are apparently no  lights on the port on the laptop, so I can not say about that.
Also, the port is enabled in the BIOS.

**Touchpad:**
It shows erratic behaviour and performance is not appreciable. I know that good touchpads are not so common but I think this can be improved. I also saw some scripts in the Dell installation regarding touchpad input.

**Battery performance:**
It was quite poor at first. But then I installed and switched off the nVidia by installing 'bbswitch'. Though, its quite better now, I would love to know of any optimizations in the Wifi chipset or anything else as I saw some scripts regarding that as well in the OEM installation.

Hoping to hear back :-)
Cheers..!

---

### Post by mveplus on 2013-07-13
> **purezen said:**
> 

**Sound:**
This is the most important issue with the laptop. The  sound output is only feeble although from what I could gather, the users  of the Windows version are not facing any such issues.

For the sound issue will continue monitor the [other post in forum]("http://ubuntuforums.org/showthread.php?t=2152776") because there already a few guys there looking for solution... 
My wife love's using Linux and now she gives me really hard time ;) because she have to use Windows instead... because of the sound!


> **purezen said:**
> **Ethernet:**
This is a one more crucial issue that I am facing. The  ethernet port is not detected by the OS. Though, when I connect the 5460  to my router via a cable, the ethernet LED lights up on the router.  However, there is no activiy in my OS. Also, there are apparently no  lights on the port on the laptop, so I can not say about that.
Also, the port is enabled in the BIOS.
I do not have any issues with Ethernet port... 

> **purezen said:**
> **Touchpad:**
It shows erratic behaviour and performance is not appreciable. I know that good touchpads are not so common but I think this can be improved. I also saw some scripts in the Dell installation regarding touchpad input.

Touchpad is annoying because it does not have right hardware button, and if change the setting and make button work touch-pad speed becomes unusable. But it irritates me as well on windows.

> **purezen said:**
> 
**Battery performance:**
It was quite poor at first. But then I installed and switched off the nVidia by installing 'bbswitch'. Though, its quite better now, I would love to know of any optimizations in the Wifi chipset or anything else as I saw some scripts regarding that as well in the OEM installation.


I do not have notice significant Battery performance lost on Linux vs. Windows. But we haven't used for longer times on battery power...

WiFi is another issue I do not like build-in one: RTL8723AE! It's sensitivity is awful, combined with build-in antennas in the body (not in the LCD pannel as usual), makes the things even worse.... So I decide to change it and use [Intel Centrino Advanced-N 6205 AGN]("http://www.intel.com/content/www/us/en/wireless-products/centrino-advanced-n-6205.html") instead ( the one I found is form OEM Lenovo, Thinkapd X220 card that works perfectly with Linux, but does not work at all in Windows because IRQ problems ). 
So now the sensitivity is great and does not drops the connections anymore ( three concrete walls away from the router) , as well I have +5G band! If you need Bluetooth you may look this [Intel 6235AN card]("http://www.intel.com/content/www/sg/en/wireless-products/centrino-advanced-n-6235.html") instead.

I'm thinking now to go back to pre-installed Ubuntu and look what changes they made and move them to my new installation as well.

Thanks to sharing your thoughts! 

Greetings

---

### Post by purezen on 2013-07-31
> **mveplus said:**
> For the sound issue will continue monitor the [other post in forum]("http://ubuntuforums.org/showthread.php?t=2152776") because there already a few guys there looking for solution... 



Sure..:)

> 
My wife love's using Linux and now she gives me really hard time ;) because she have to use Windows instead... because of the sound!



Yeah.. Understand that..

> 
I do not have any issues with Ethernet port... 



I will check that again..

> 
Touchpad is annoying because it does not have right hardware button, and if change the setting and make button work touch-pad speed becomes unusable. But it irritates me as well on windows.



Hmm..

> 
I do not have notice significant Battery performance lost on Linux vs. Windows. But we haven't used for longer times on battery power...

WiFi is another issue I do not like build-in one: RTL8723AE! It's sensitivity is awful, combined with build-in antennas in the body (not in the LCD pannel as usual), makes the things even worse.... So I decide to change it and use [Intel Centrino Advanced-N 6205 AGN]("http://www.intel.com/content/www/us/en/wireless-products/centrino-advanced-n-6205.html") instead ( the one I found is form OEM Lenovo, Thinkapd X220 card that works perfectly with Linux, but does not work at all in Windows because IRQ problems ). 
So now the sensitivity is great and does not drops the connections anymore ( three concrete walls away from the router) , as well I have +5G band! If you need Bluetooth you may look this [Intel 6235AN card]("http://www.intel.com/content/www/sg/en/wireless-products/centrino-advanced-n-6235.html") instead.



Well, I shall stick to the stock for now..

> 
I'm thinking now to go back to pre-installed Ubuntu and look what changes they made and move them to my new installation as well.



Sure. Keep us updated..!!

> 
Thanks to sharing your thoughts! 

Greetings

My pleasure..:)

---

### Post by Vincent Tham on 2013-08-11
I've purchased the Dell Vostro 5460 Intel i3 with Ubuntu 12.04 preinstalled.  I've updated all the ubuntu update manager packages, but I'm still having same low volume for audio.  I've tried the alsamixer and turn up the main volume but the problem still persisted.  As an alternative, I've used a Bluetooth speaker for the time-being.

Looking for a solution to fix this issue.

---

### Post by Mnxa on 2013-08-17
Mine Dell Vostro 5460 had ubuntu 10.10 preinstalled. I switched to 12.04. Performance is not bad, but every other time it boots with black screen (nothing-system is not responding to anything except the power button). Any Ideas?

---

### Post by purezen on 2013-08-17
Hey guys..!

I have filed a bug regarding the low audio output at: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1211920](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1211920)
If possible contribute something there, like atleast confirming that the bug affects you..!

Cheers..:)

---

### Post by Nairph on 2014-04-05
I have update the kernel to 3.11 version and the sound is better and louder, but still not at the best performance. Maybe we can wait for 3.15 kernel.
[http://www.phoronix.com/scan.php?page=news_item&px=MTY1MDg](http://www.phoronix.com/scan.php?page=news_item&px=MTY1MDg)

---

