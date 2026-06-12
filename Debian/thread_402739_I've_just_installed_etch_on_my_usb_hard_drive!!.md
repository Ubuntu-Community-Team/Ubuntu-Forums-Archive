---
title: "I've just installed etch on my usb hard drive!!"
date: 2007-04-06
forum: Debian
---

### Post by Pugwash on 2007-04-06
Hi,

I just want to get this off my chest, I feel it is a landmark in my short time with linux so far.  I've been quite curious about the big daddy since I first started researching ubuntu. I heard all the talk about it being one of the traditional distros aimed for the linux veterans and connoisseurs. But last night, my curiosity got the better of me and I went off to the debian site and downloaded the Amd64 netinstaller and burnt it (Its my first foray into the world of 64 bit as well) hoping to install it on my external usb hard drive (if such a thing was possible). I wanted to build it lean and mean, so decided to do the basic install without the desktop and then add xfce and some packages I wanted on top . I was quite sure I was going to totally trash my laptop but the decision had been made. So, I rebooted and started the install, it flew by suprisingly quickly without any major hitches (actually, it didn't create a swap partition for some reason, probably because I installed it on an external but I carried on). 

The installation completed and rebooted my computer. I  sat there awaiting the damage that was caused.... Grub loaded (phew).... but then I noticed a conspicuous absence of the ubuntu kernels in the menu (the menu screen was nice and blue though) before debian started to load. Aaah crap! I sat there completely dejected for a while. I saw the command line blinking at me (no major problems there it seemed at least), and I thought of solutions. I restarted again and the same situation presented itself, ubuntu had disappeared! I decided to whip out my ever reliable dapper live cd and take a closer look at the mess I created.... Booted into the liveced and confirmed that my ubuntu installation was still present on my internal hd ( a big relief). Proceeded to  mount the ubuntu partition and had a look a look at the menu.lst file in the grub folder, no changes there it seemed and no mention of any Debian kernels. Went into my usb hard drive and looked into the menu.lst file where it listed the debian kernels. My laptop was loading from the grub file from the debian install in the usb drive. A long shot but I copied  the kernel list from Ubuntu to the debain grub file, and restarted.... And that seemed to have solved it ( at least temporarily, thats where you guys can help me out I hope, I can't eject/unmount my USB drive through gnome/nautilus/thunar in ubuntu). 

Went back to debian and installed the basics which I gleaned of the net:

aptitude update
aptitude install x-window-system-core xfce4 gdm firefox
reboot

Then I was met with an exceedingly pretty, blue, fast xfce desktop (boy is it fast, I've not even installed the ati drivers yet). So there's my story!  Any advice on how to get grub to point to the menu.lst in my ubuntu installation in my internal hard drive  would be greatly appreciated. 

Now for some well-needed sleep.:lolflag: 

Cheers

---

### Post by teaker1s on 2007-04-06
grub will need editing or you cold try "super grub" live iso and see if it can fix it.

I've Debian etch and I've noticed that some debian packages install and need system configured eg. loading modules-ubuntu the package script does it for you:KS

Etch I'm running Beryl on

---

### Post by Rodneyck on 2007-04-06
Etch will be unfrozen in hopefully a few days. They were going to release the new version on April Fool's Day, but needed an extra week to hit some more bugs.

If you really want to step up to the next level after Etch, try Sidux. This is my primary distro and it is very fast. Debian Sid made stable...but the stuff is cutting-edge so there is no guarantee. It will be even more cutting edge when Etch unfreezes, and all the packages being held back as a result, drop into Sid.

[www.sidux.com](www.sidux.com)

---

### Post by Pugwash on 2007-04-08
I managed to fix grub doing this - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) . I'm very impressed with etch but I can't seem to get the Ati drivers installed, not much documentation on the net to do it properly. I'll have a look at sidux when I get some free time, thanks for the info Rodneyck

---

