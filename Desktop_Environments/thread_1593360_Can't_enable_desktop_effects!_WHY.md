---
title: "Can't enable desktop effects!? WHY?"
date: 2010-10-11
forum: Desktop Environments
---

### Post by 3startuna on 2010-10-11
Hi guys I'm having a weird problem. 

I have a Nvidia Geforce 8400GS card installed.

I just reinstalled Ubuntu 9.10 on my computer, everything works but I can't enable desktop effects. I tried using the generic drivers in synaptic nothing. Tired the restricted drivers, (both of them) the system runs smoother, but still can't enable desktop effects.

I tried upgrading to 10. And after the upgrade and restart I just got a black screen. I couldnt even access the terminal So I went back to 9.10.

I ran the compiz-checker script. And it spit back 

" More than one graphics chip detected -- sorry, the script can not handle that.
 Aborting."

Which lead me to believe the onboard card was still enabled. Unfortunately I can't disable it in bios as my bios doesn't have that option.

Word of the weekend = FAIL :(

Help please

---

### Post by ankspo71 on 2010-10-11
Hi,
Do you have the same problem in other Linux distributions, Windows, or Mac?

Shutdown first, then double check to make sure that you have the monitor plugged into the Nvidia 8400GS card, and not the onboard graphics. I made that mistake a couple of times after moving my computer to different rooms - the result was a black screen. I believe on my computer, as soon as I installed my second graphics card and plugged my monitor into it, the onboard graphics card automatically disabled itself. I don't appear to have a way to disable either of my graphics cards in the bios too... or maybe I just can't find that option.

I have VIA Chrome9 graphics (onboard and disabled as far as I know), Nvidia 8400GS graphics (pci-e x16), on a Biostar P4M900-M4 motherboard + Phoenix Award Bios. The Nvidia card works with either the opensource or the non-free drivers with effects enabled.

I hope this helps.

---

### Post by ankspo71 on 2010-10-11
Hi,
Can you post the contents of your /etc/X11/xorg.conf file? 
It might be trying to load the wrong (or both) drivers. Since you currently have a black screen you will probably want to use your Live CD to access that file from your hard drive. I'm not an expert on xorg, but posting the contents of that file could help other people find the problem for you.

---

### Post by 3startuna on 2010-10-11
Just checked it again. I am plugged into the Geforce.

Desktop effects worked well with 9.04 and the older 8 distro when I Had them installed. 

I stored my computer with a friend and my hard drive got damaged so I had to do  a fresh install with 9.10.

Everything works fine except desktop effects. Infact im typing from my computer right now. 

I got the blackscreen when I tried the 10.04 LTD upgrade

Heres the contents of /etc/X11/xorg.conf file

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

Thanks for all the help guys

---

### Post by ankspo71 on 2010-10-11
Hi Again,
Your /etc/X11/xorg.conf file looks good. It is exactly the same as mine. 

Do your graphics become enabled when you run this command in the terminal?
```
compiz --replace
```
If the desktop effects don't start, or quit after some time, what do the error messages say?

---

### Post by 3startuna on 2010-10-11
running compiz --replace give me this 

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by 3startuna on 2010-10-11
Problem solved!

I disabled the blacklist checks and everything runs pewrfect!

Thanks for the help

[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by ankspo71 on 2010-10-11
I'm glad you got it working. :) 

Strange...I haven't seen my card get blacklisted yet. It might have to do with the combination of hardware then.

---

