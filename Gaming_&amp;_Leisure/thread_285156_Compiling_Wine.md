---
title: "Compiling Wine"
date: 2006-10-26
forum: Gaming &amp; Leisure
---

### Post by gerowen on 2006-10-26
When I ran FC5 I could play WoW in Wine, and now that I've installed Edgy I figured I'd do the same thing.  Well apparently the new version of wine is 0.9.23, one version newer than the one I used.  When I do ./configure it bumps down a few lines and checks a few things, then cancels out with "C Compiler Cannot Create Executables".  Help anybody?

---

### Post by gerowen on 2006-10-26
Problem solved, didn't have g++ installed by default, now I'm just going through the process of:
./configure
Read and install missing dep
Repeat 50 times until done

---

### Post by Jorenko on 2006-10-26
> **marcusdean.adams said:**
> Problem solved, didn't have g++ installed by default, now I'm just going through the process of:
./configure
Read and install missing dep
Repeat 50 times until done

you might want to try `sudo apt-get build-dep wine`

Also, they provide a script to do the build for you now too. `./tools/wineinstall`

---

### Post by x01000100 on 2006-10-27
Hello mate, you might wanna read this ;)
[http://www.ubuntuforums.org/showthread.php?t=285014](http://www.ubuntuforums.org/showthread.php?t=285014) (

> Download this, a prepatched wine for wow [http://thepiratecove.org/files/wine-0.9.21_wow_i386.deb](http://thepiratecove.org/files/wine-0.9.21_wow_i386.deb) Rightclick it and select install package. Done. :)

Good luck and happy hunting!8)

---

### Post by gerowen on 2006-10-27
> **x01000100 said:**
> Hello mate, you might wanna read this ;)
[http://www.ubuntuforums.org/showthread.php?t=285014](http://www.ubuntuforums.org/showthread.php?t=285014) (



Good luck and happy hunting!8)

Hey I'm keepin' that file around.  I installed wine with it, then just updated when synaptic started yelling at me from the system tray, and the nvidia fix kept with the update to 0.9.22.  Thanks a ton!

---

### Post by reiki on 2006-10-28
Not sure how you managed to keep the fix when you upgraded, but that didn't work for me. When I upgraded, the fix disappeared. However I will be satisfied for now that with that prepatched 9.21 version, I can play WoW in Edgy. I may build a 9.23 patched version myself here.

---

### Post by gerowen on 2006-10-28
Yeah I "thought" it kept.  There was no flickering on the title screen or in the Sepulcher where I was, but when I ported to Orgrimmar the flickering started again.  Not sure why it waited, before when I installed .22 without the patch it flickered even on the title screen.  Meh, I'll have to try and compile it again.

---

### Post by reiki on 2006-10-28
I was going to make a .deb of 9.23 prepatched for nvidia, but I've never made a deb before and so I started compiling here :)

I'll see how it goes.

Takes a while. And I'm on a dual core with 2 gigs of ram. Should be interesting.

---

### Post by reiki on 2006-10-28
ok I've managed to screw this up pretty badly. The compiled version of 9.23 segfaults, I tried to reinstall and uninstall 9.22 using synaptic and also tried to install and remove 9.21 from teh prepatched .deb. Wine is completely broken on my machine.

Here's what I learned. Compiling 9.23 is not my friend.
9.22 as it stands in the repositories for Ubuntu does not work
The .deb that is prepatched 9.21 works and I should have left it alone :)

---

### Post by Protoss on 2006-10-28
The segfault is a problem with some GCC flag. [https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965](https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965)
I couldn't get it to compile either. If someone could get 0.9.24 patched and packaged, that would just rock.

---

### Post by gerowen on 2006-10-28
Well, I've got 0.9.24, but I can't seem to find the nvidia patch.  Maybe it doesn't need one?  I know after version 0.9.21 an ati patch was no longer mentioned, so maybe they fixed the need for a patch for nvidia cards this time around.  I'll compile it and see how it goes.

---

