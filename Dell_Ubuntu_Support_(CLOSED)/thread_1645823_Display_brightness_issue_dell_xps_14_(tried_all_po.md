---
title: "Display brightness issue dell xps 14 (tried all posted solutions)"
date: 2010-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by niken15 on 2010-12-15
Hello
I have a dell xps 14 with nvidia 450m graphics card.  I am running ubuntu 10.10 on it. My display brightness control hotkeys do not work and I get the maximum brightness by default. I have tried all possible solutions I found on different forums including [http://ubuntuforums.org/showthread.php?t=1636959](http://ubuntuforums.org/showthread.php?t=1636959) and a bunch of others mentioned here [B][URL="http://groups.google.com/group/sjslug/browse_thread/thread/ede5fd158be7eeba/923bce788100ca18?lnk=raot&pli=1"]http://groups.google.com/group/sjslug/browse_thread/thread/ede5fd158be7eeba/923bce788100ca18?lnk=raot&pli=1
[/URL]
In my  [/B]/proc/acpi/video/GFX0 folder I have a folders from DD01 to DD08 each having a brightness.txt file which says '<not supported>' So i cannot write values there and commands like xgamma give error ''unable to open display ''  

I also installed the PPA from here [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)
But i only see the Dell backlight folder in /sys/class/backlight folder and not the intel backlight as described. 

The max brightness is killing my eyes and i cannot work. Please help me solve this problem

---

### Post by krunalpatel on 2010-12-16
> **niken15 said:**
> Hello
I have a dell xps 14 with nvidia 450m graphics card.  I am running ubuntu 10.10 on it. My display brightness control hotkeys do not work and I get the maximum brightness by default. I have tried all possible solutions I found on different forums including [http://ubuntuforums.org/showthread.php?t=1636959](http://ubuntuforums.org/showthread.php?t=1636959) and a bunch of others mentioned here [B][URL="http://groups.google.com/group/sjslug/browse_thread/thread/ede5fd158be7eeba/923bce788100ca18?lnk=raot&pli=1"]http://groups.google.com/group/sjslug/browse_thread/thread/ede5fd158be7eeba/923bce788100ca18?lnk=raot&pli=1
[/URL]
In my  [/B]/proc/acpi/video/GFX0 folder I have a folders from DD01 to DD08 each having a brightness.txt file which says '<not supported>' So i cannot write values there and commands like xgamma give error ''unable to open display ''  

I also installed the PPA from here [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)
But i only see the Dell backlight folder in /sys/class/backlight folder and not the intel backlight as described. 

The max brightness is killing my eyes and i cannot work. Please help me solve this problem


Make sure you read the entire PPA ([https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)) and make sure that it actually does qualify in your case. If it does, email Kamal and ask talk to him. He was very helpful to me.

---

### Post by turbojatt on 2010-12-20
Hi 
Could you solve your issue.
I have the similar problem with Dell inspiron 14R and ubuntu lucid lynx. The PPA mentioned for the fix for this bug is for ubuntu 10.10 and higher if I am not wrong.

Any suggestions?

---

### Post by Carlmon on 2011-04-30
I'm not running 64 bit, but I found something that might help. You could install a compiz configurator and do what I did. I used the xcalib function and assigned the different commands to the brightness keys via compiz command lines. I hope you can figure out my post. I ain't so good at 'splainin all this mess. I'm just good about finding workarounds. See the attachment.

---

### Post by alefromhell on 2011-06-01
i also have a xps 14 and am running x64 ubuntu, just here to say that Carlmon's solution worked[U]
[/U]

---

### Post by djest on 2011-11-28
Good day, guys.

This solution is not the same as it should be with standard buttons behavior.
It decrease/increase brightness but not contrast.
So it looks not good for eyes by this way.
Maybe it is just on my machine.

I have dell xps 15 501x with Ubuntu 11.04 installed.

---

