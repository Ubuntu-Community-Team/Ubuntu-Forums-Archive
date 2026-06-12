---
title: "Could these problems be caused by a 64-bit installation?"
date: 2009-02-26
forum: General Help
---

### Post by Itchyfinga on 2009-02-26
Ubuntu offers 8.1 in 64-bit, and, having verified that my Acer desktop is equipped with an AMD Athlon 64-bit dual-core, I decided to see what ubuntu's matching-bit system could do for it's performance. I'm not sure that I've ever seen what a 64-bit processor should be able to do, because my factory-installed operating system is Vista Home Premium 32-bit! Well, I did consider that there could be a reason for this, but could think of none which would'nt make the use of a 64-bit processor in my system, as it was produced by Acer, altogether pointless. Then again, I know very little about hardware configuration, and would much appreciate the insight of those who know this stuff. 

I installed ubuntu (no x or k, so I think it's GNOME-based) "to run in Windows", which resulted in a dual-boot. 

When I tried to change the screen resolution, I lost my menus, and the screen went dark. When I change the background picture, ubuntu forgets it when I restart. When I installed flash plugins, ubuntu goes through the motions, and even recognizes that they have been installed (when I try to install them again), but it incessantly keeps hitting me up with the same "need to install" prompts!  Not quite the smooth ride which I was led to expect, but then I did choose the 64 bit (and why shouldn't that work in my system, andyway) - please help if you are aware of any 64-bit issues, be it the ubuntu 64 version, the AMD Athlon dual-core, or the possibility of other causes.

Thanks.

---

### Post by cd-r80 on 2009-02-26
I have Acer 5520 AMD Dual & 64bit Xubuntu. Everything seems to work. Allthought I haven't checked all. Perhaps it is a Gnome thing.

p.s
I run gnome services too.

---

### Post by linux4me on 2009-02-26
What you're experiencing doesn't sound like 64-bit issues. They may be installation issues. It almost sounds like you're running Ubuntu in a virutal machine rather than as a dual boot setup. When you did the install, did you boot from the Live CD or start the Live CD from within a running Windows session?

Most of your 64-bit questions can be answered in the [64-bit forum]("http://ubuntuforums.org/forumdisplay.php?f=343"), and specific instructions (very easy) for installing the 64-bit version of flash player can be found [here]("http://ubuntuforums.org/showthread.php?t=772490").

I recommend reading through this [dual-boot install Wiki]("https://help.ubuntu.com/community/WindowsDualBoot") to make sure you did everything correctly with the install, too. You can find all the installation instructions for other methods of installation [here]("https://help.ubuntu.com/8.10/installation-guide/amd64/index.html").

I have had some problems myself with the 64-bit version of 8.10 on one machine, but they were problems of program stability and small niggles, not major. For it, I run 8.04 64-bit and it is stable and problem-free.

---

### Post by jespdj on 2009-02-26
> **Itchyfinga said:**
> Ubuntu offers 8.1 in 64-bit, ...
It's not Ubuntu 8.1, but 8.10. The version number indicates the year and month that this version was released: 8 = 2008, 10 = October.

64-bit Ubuntu is really not that different from 32-bit Ubuntu. People too often blame vague problems on the fact that they're running the 64-bit version, while they really have no clue what the true cause of the problems is. 64-bit is not less stable or polished than 32-bit. There's no reason at all to assume that the problems you see have anything to do with 64-bit.

What video card do you have and what video driver are you using?

---

### Post by kevinatkins on 2009-02-26
Hi,

Your Flash problems may be to do with the 64-bit version - I'm not 100% sure, but I know certain application software doesn't work well in a 64-bit environment. It's also one of the reasons that Acer will have pre-installed a 32-bit flavour of Vista - support for 64-bit isn't complete.

I have to say, I did try just what you've tried on my dual-core Athlon 64-bit system about 18 months ago, and run into a few problems... I went back to 32-bit Ubuntu, and frankly didn't notice much (if any) hit on performance, so I'd suggest sticking with 32-bit for the time being.

---

### Post by mb_webguy on 2009-02-26
> **jespdj said:**
> It's not Ubuntu 8.1, but 8.10. The version number indicates the year and month that this version was released: 8 = 2008, 10 = October.

64-bit Ubuntu is really not that different from 32-bit Ubuntu. People too often blame vague problems on the fact that they're running the 64-bit version, while they really have no clue what the true cause of the problems is. 64-bit is not less stable or polished than 32-bit. There's no reason at all to assume that the problems you see have anything to do with 64-bit.

What video card do you have and what video driver are you using?

+1

I'm using 64-bit Intrepid on my Intel Core 2 Duo Dell Inspiron, and I've actually had fewer problems than I did with 32-bit Intrepid or Hardy.  Once upon a time, when 64-bit processors were still new to the market, support for them was fairly poor.  But that's not the case any more.  Even Flash, which most people point out as being the one weak point in terms of 64-bit support, works perfectly for me with the official Adobe alpha-release 64-bit plugin -- and considerably better than it did in 32-bit Hardy.

---

