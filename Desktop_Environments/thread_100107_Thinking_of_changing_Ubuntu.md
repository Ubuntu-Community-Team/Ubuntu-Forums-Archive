---
title: "Thinking of changing Ubuntu?"
date: 2005-12-06
forum: Desktop Environments
---

### Post by rozojc on 2005-12-06
Well, I am extremely happy with this distro and yet I'm thinking of changing it... why? haven't been able to solve my freaking problem with Xorg. I recently posted asking for help with this, but got few replies and I wasn't able to fix anything. After a couple of hours Xorg just fires up my processor to 100% and things get slowish...

I checked with "top" and Xorg is the process that consumes everything. I tried installing "treeps" to check out all processes and again the process eating resources is exclusively the process called Xorg...

Any ideas? I'd hate changing Ubuntu, but I don't really like having the processor going at 100% all the time and listening to the fan the whole day long (my laptop is on for a great part of the day)...


Ideas anyone?

---

### Post by aysiu on 2005-12-06
Change.
Ubuntu isn't the be-all and end-all of Linux or operating systems in general. If it works for you, great. If not, try something else.

Some people will fight with Ubuntu for days or weeks to get it work. I say, why? Libranet didn't recognize my mouse or my sound. I spent about an hour with Libranet. Tried something else.

Luckily, there are a lot of live CDs out there, so you can try stuff out before going the full install. I'd highly recommend PCLinuxOS or Mepis.

---

### Post by nix4me on 2005-12-06
I have seen some reports of this in these forums.  Try a forum search of of 'xorg' and see what you find.

nix4me

---

### Post by aysiu on 2005-12-06
[QUOTE=nix4me]I have seen some reports of this in these forums.  Try a forum search of of 'xorg' and see what you find.[/QUOTE] [This is the most comprehensive guide to xorg I've seen on these forums](http://ubuntuforums.org/showpost.php?p=129379&postcount=21). If that doesn't work for you, Ubuntu probably isn't for you (or your computer, at least).

---

### Post by rozojc on 2005-12-06
Well, I just checked the forums and yes, this thing has come up several times. Nobody seems to have solved it...

Some people reported that a kernel upgrade could help, however I am using the latest kernel... I have a Sempron processor, I suppose I could change kernel to K7, and see if that works, right?

Besides that I just read a couple of postings of people reporting the problem but being unable to solve it...

Oh well, I guess I'll try the kernel upgrade and if nothing works I'll think about switching to Vector, Slax, Ark or something like that (I don't really like MEPIS or PCLinuxOS)

Any other ideas are welcome.

---

### Post by Stavroghin on 2005-12-09
Hi. I've had the same problem with the Xorg consuming CPU. But i finally managed to make it work.
First, when you install ubuntu, do that like this: "install ubuntu vga=771 noapic nolapic". The install process will go a lot faster. The problem with Xorg (can't start) remains. All you need is to install the new ati driver. This: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) will explain to you what to do. You need to download the version 8.20.8 (that worked for me). 8.16 has some bugs.
After you configure fglrx (fglrxconfig) appears another problem. The xorg.config file is not corect. It misses "EndSection" at the end of the file and a < Section "Screen" >.
It looks like this:

Section "Screen"
          Identifier   "Default Screen"
          Device      "Ati Graphics Adapter" #that is what i've got, look in the                                                  #same file at the section device
          Monitor    "Monitor0" #look in the section Monitor
          DefaultDepth         24
          SubSection     "Display"
                      Depth        24
                      Modes       "1024x768"
          EndSubSection
EndSection

Use tabs for like it is done in the config file.
After that restart gdm (/etc/init.d/gdm restart).

I hope I haven't forgot something. Now the Xorg consumes under 1% of the CPU and before (when i installed without those parameters) the procentage was above 20.
By the way, I have a HP nx6125 Turion ML-34 1.8GHz.

---

