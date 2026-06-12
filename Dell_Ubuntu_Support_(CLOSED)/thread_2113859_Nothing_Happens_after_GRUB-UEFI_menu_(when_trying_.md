---
title: "Nothing Happens after GRUB-UEFI menu (when trying to install Ubuntu with Windows 8)"
date: 2013-02-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by HectorHSS on 2013-02-08
Hello everyone,

I have never installed ubuntu before, after some tries (some mess-ups) and reading some documentation I see that a pre-installed with windows 8 laptopt is a bad place to start... but well here I am and what is happening is the following:

- I downloaded Ubuntu 12.10 for 64bits and used unetbootin to make a bootable USB.
- When booting with this USB on UEFI mode I can see the plain menu (dark background, white text) with the options:
    * Try Ubuntu
    * Install Ubuntu
    * OEM install
- Choosing Try Ubuntu or Install Ubuntu will lead me to a dark screen and after several seconds reading USB stick, it will just stop and do nothing afterwards.

I have tried different setups based on what I have found in forums: disabling secure boot, changing Intel Smart Response Technology to ATA, both together.

When I try to load with Legacy mode I can load Ubuntu correctly, so USB stick is fine.

I am trying on a Inspiron14z 5423.

I am not sure which other information would be valuable so feel free to ask (of course).

---

### Post by oldfred on 2013-02-08
Usually the dark screen after system does seem to start is a video driver issue. Several versions ago LInux added video to kernel from usermode and ever since I have had to use nomodeset to avoid black screen on live installer boot and first boot after install until I get the proprietary nVidia driver installs. Sometimes it also can be other boot parameters instead or also.

What video does your system have. nomodeset may work for most, but some require other settings.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
From the try Ubuntu screen can you press f7 or e. Not sure with UEFI which works. Then add the nomodeset boot option or replace splash quiet on linux line with nomodeset. Screen shots in above links to show what it may look like.

If you also have an Intel SRT system that even makes it more complex. But lets see if you can just get it to boot in live mode first.

Other Dell's that have worked, so UEFI may be similar, but each system may have differences.
       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by altieresdelsent on 2013-03-30
I have the same issue with the exact same model, I tried nomodeset, still the same problem, what else can I try? I try any option( try ubuntu, install ubuntu, OEM install) , the screen became black, stay black for 5 minutes and after it return to the first menu ( try ubuntu, install ubuntu, OEM install), I tried with 12.04, 12.10 and 13.04 beta, all of these, still is the same problem, I tried deactivate secure boot and still the same problem. The strange is that when i install in a virtual machine inside windows 8, everything works fine... I really don't know what to do... what else can I do? I am downloading sabayon to see if this a ubuntu problem or a general linux problem..

---

### Post by oldfred on 2013-03-30
Other Dell systems. IF an Ultrabook model you also have issues of Intel SRT (remove RAID) and dual video not supported by nVidia(use bumblebee).

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

