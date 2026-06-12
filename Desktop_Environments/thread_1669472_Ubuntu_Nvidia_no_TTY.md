---
title: "Ubuntu Nvidia no TTY"
date: 2011-01-17
forum: Desktop Environments
---

### Post by aceralex on 2011-01-17
Hi all, 
 i am running ubuntu 10.10 with awesome and gnome (gnome for testing reason). I  have the problem that i can't change from my Windowmanager (**Awesome +  Gnome** , both are affected by this problem) to any tty (Displaymanger ** Slim**). All tty's are listed on /dev as they should. 
A change to any tty cause all sound (pulseaudio) to stop till i change back to wm  (alt + ctrl + f7) and then when i hit return slim crashes. Sometimes then  i see a lot of black squares in screen and blinking cursor (i guess  from tty in background).  I am using slim as displaymanager. 

I also tried gdm with a different behaviour regarding that problem: 
In **gdm** i am able to switch to tty but when i watch flash in fullscreen  and switch of fullscreen the last movieframe is freezed on some parts of  the windowmanager's gui (desktop, panel etc).  

I figured out, that booting in single user mode (grub -> single)  fixes the strange behaviour.  This strange behaviour is hard to  describe, i hope anyone has a similar problem/experience. 

Thanks in advance. 

------------------------------
Additional Information:
------------------------------
System: Ubuntu 10.10 64bit kernel 2.6.35-24-generic 
GFX Card Nvidia GT 430  
GFX Driver nvidia-current 260.19.06   

Grub legacy (for Dual Boot/Crypt reason) 
/boot/grub/menu.lst:  
```

[...] 
title           Ubuntu 10.10, kernel 2.6.35-24-generic uuid             bbff97c3-dbf0-4195-9638-a9e32e976dcd 
kernel           /vmlinuz-2.6.35-24-generic  root=UUID=16564a52-bc0f-4603-bff4-3520866e4585 ro quiet splash initrd          
 /initrd.img-2.6.35-24-generic quiet

```

---

### Post by aceralex on 2011-01-23
The following Screenshot attached shows the Problem after using the flashplugin in my browser. The black area, showing the flash movies's last picture remains after closing the flashplayer. In a screenshot via scrot it doesnt appear, so i took a photo of my screen.

---

### Post by Krytarik on 2011-01-23
Check the behaviour if you run the default open source driver for Nvidia devices instead of the proprietary one, by replacing "nvidia" with "nv" in /etc/X11/xorg.conf. How did you install the driver, via "Additional Drivers" or in another way?

---

### Post by aceralex on 2011-01-23
hi,
i installes the "original" nvidia drivers via apt-get install nvidia-current.

cheers.

---

### Post by Krytarik on 2011-01-23
> **aceralex said:**
> hi,
i installes the "original" nvidia drivers via apt-get install nvidia-current.

cheers.
Ok, that explains some! Switch to the "nv" driver as mentioned.
Then remove that package with:
```
sudo apt-get remove --purge nvidia-current
```
Then install it again via "System -> Administration -> Additional Drivers", which will pull in some other packages.

After that, and hopefully a successful reboot, save the configuration to the "xorg.conf":
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

---

### Post by aceralex on 2011-01-23
ok, but i need 3d [I]acceleration, does it works with the nv driver?
[/I]

---

### Post by Krytarik on 2011-01-23
> **aceralex said:**
> ok, but i need 3d [I]acceleration, does it works with the nv driver?
[/I]
Nope, that's why you to do the other steps as well.;)

---

### Post by aceralex on 2011-01-23
okay thanx, now i got it :D
i will try and post my experience with that

---

### Post by aceralex on 2011-01-24
ok, i was able to fix closely everything. after following your  instruction, xserver failed to start with various errorlogs. the i  installed the latest nvidia-driver from ubuntu-x-swat. that did it, now i  am able to use my tty's and everything's fine except  *surprise' flash !

But the reason for that failing is flash itself because of its failing ..... time for webm xD

just for your amusement, the latest behaviour of flash :popcorn:

thanx for your help and inspiration, krytarik 8)

---

### Post by Krytarik on 2011-01-24
Yeah, Flash definetely sucks, it's overly heavy CPU-consuming. I tend to give Apple right to not supporting it. Although I don't have such a mess like you in the screenshot. You may try those guide, altough it doesn't work for me, maybe because I've a bit old hardware setup:
[http://ubuntuforums.org/showthread.php?t=1645908](http://ubuntuforums.org/showthread.php?t=1645908)

---

### Post by aceralex on 2011-01-29
hi,

good news, flashplayer 10.1.102.65 sucks a bit less, it works as you can call flash working, no burned frames and blacksquares anymore.

greets, aceralex

---

### Post by Krytarik on 2011-01-29
> **aceralex said:**
> hi,

good news, flashplayer 10.1.102.65 sucks a bit less, it works as you can call flash working, no burned frames and blacksquares anymore.

greets, aceralex
Oh, I already had those version, I assumed that you also had the most recent updates.
I checked the log of apt, it has been installed exactly at 2010-11-19 at my machine.[-X ;)

If you want to mark this thread as "solved", do it via "Thread Tools", thanks.

---

### Post by aceralex on 2011-01-30
> krytarik wrote:
Oh, I already had those version, I assumed that you also had the most recent updates.
I checked the log of apt, it has been installed exactly at 2010-11-19 at my machine.[-X :wink:Hmm thats strange i update my system usually at least once a week, so i assumes to have the latest version already, but maybe its because of my amd64 ubuntu.

cheers, aceralex

---

### Post by Krytarik on 2011-01-30
> **aceralex said:**
> Hmm thats strange i update my system usually at least once a week, so i assumes to have the latest version already, but maybe its because of my amd64 ubuntu.

That makes indeed totally sense, I didin't take that into account, Adobe's development of the 64-bit Flash plugin is lagging behind those of its 32-bit version.

That also explains the major difference of its performance between your and my machine.

Adobe states to have a preview version here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) . I only get 32-bit versions displayed there, I suppose because my browser reports itself at 32-bit.

If that URL doesn't work for you also, here is another one, same version:
[http://fileforum.betanews.com/detail/Adobe-Flash-Player-for-Linux/964714156/4](http://fileforum.betanews.com/detail/Adobe-Flash-Player-for-Linux/964714156/4)

This should provide a considerable performance increase, because of its native 64-bit support.

The version you are currently getting through the repo is imo just a port to 64-bit.

---

