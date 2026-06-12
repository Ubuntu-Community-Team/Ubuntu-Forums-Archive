---
title: "Intrepid locks up at random."
date: 2009-02-24
forum: General Help
---

### Post by KHicks on 2009-02-24
32-bit 8.10 installed on an Athlon 64.
nVidia graphics card with proprietary driver.
Gnome desktop.
ALSA sound.

The entire system freezes at random for no discernible reason.  The cursor sticks; there is no response to the keyboard and no recourse but a hard power cycle.  There are no indications of trouble, no kernel panics, no stack dumps, nothing, hence no diagnostic information.

What can you suggest?  What additional information do you need?

Thank you.

P.S. Feisty never crashed.  I'd still be using it if the repositories hadn't been taken offline.

---

### Post by ewz on 2009-03-02
I had the same problem a few versions back and different Distros as well, the fix I found was to add this line to the /etc/X11/Xorg.conf file under Devices **Option "NvAGP" "1"** 

Have a look at this [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-f.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-f.html) 

Hope this Helps :-)

---

### Post by nova47 on 2009-03-08
Has anyone found any other solutions to this problem? I tried the one above and my computer is still crashing so frequently that it's unusable.

---

### Post by jwbrase on 2009-03-09
Well, for lockups and such, one of the first suspects is overheating. Take a look inside your case and see how much dust is in there. If it's really dusty, try vacuuming it out. (Although be careful that you don't give a static zap to anything inside in the process).

---

### Post by ivotron on 2009-03-09
Hi,

I started to experience this 3 days ago. No matter what I'm running, the system freezes. Do you know if there's a bug report for this issue? Have anyone found a fix to this?

This thread also reports this [http://ubuntuforums.org/showthread.php?t=983459](http://ubuntuforums.org/showthread.php?t=983459)

---

### Post by nova47 on 2009-03-10
I'm beginning to think this is an issue with some sort of update. I definitely know it's not overheating, I actually just finished building the computer I'm using and it's got a 25 cm fan, a couple of 10-12 cm fans, each GPU has a fan etc. Anyway when I originally installed Ubuntu I had no problems and I also didn't start having problems until well actually now that I think about it three days ago.

---

### Post by bigken on 2009-03-10
graphics drivers would be my 1st thoughts second ram chip gone bad

---

### Post by kfenton on 2009-03-10
I had 8.10 and it was locking up at random like that.. was my wireless card. couldn't find a fix for it. switched back to 8.04..

---

### Post by nova47 on 2009-03-11
You know now that I think about it I'm pretty sure I just added a wireless card on Friday. I think I'll go check that out. I'll edit this when I find out if that's the problem.

Edit: I went ahead and took the wireless card and discovered that that is most definitely the issue. I've been running Ubuntu without any problems for over 22 minutes whereas before I never made it over 5 minutes. I tried putting the card back in and sure enough it started freezing again. For anyone else having this problem I'm running a Linksys Rangeplus adapter model number WMP110 you may try taking that out of your computer and then testing Ubuntu. I'll write back if I come up with a solution.

PS: haha I'm also pleased to see there's at least one other person that went/is at a military school that's interested in computers. Nerd that I am I pretty much get an infinite amount of crap for it from my BR's and former cadre for that matter. (Breakout was in February :-D)

---

### Post by kryptikos on 2009-03-11
Just curious, what kernel version are you using and current nvidia driver you are using? I would be surprised that a wireless card would cause your entire box to just freeze. Since you are using X (gdm) then I would lay money on that configuration as well. 

Oh yeah...nice to see a brother rat. Well...can't say I was a rat. I was a knob at The Citadel. But then again, we were sister institutions. Noticed the salt and pepper first before I noticed the signature. Haha, I will say the salt and pepper were sharp. The girls always noticed that. Although I hated the chicken bucket during pass n reviews. Preferred the cap. Best of luck to you and your endeveaors!

---

### Post by ivotron on 2009-03-11
> **kryptikos said:**
> Just curious, what kernel version are you using and current nvidia driver you are using? I would be surprised that a wireless card would cause your entire box to just freeze. Since you are using X (gdm) then I would lay money on that configuration as well

I'm using

Kernel: Linux 2.6.27-13-generic #1 SMP Thu Feb 26 07:31:49 UTC 2009 x86_64 GNU/Linux

Nvidia: 180.11-0ubuntu1~intrepid1

Wireless: 2009-03-10 compatibility drivers from [http://wireless.kernel.org](http://wireless.kernel.org)

On the /var/log/messages log, the last thing that gets logged before the system freezes are wireless messages.

Yesterday night I started a test and disabled the wireless drivers and plugged the ethernet cable. No freezes so far. I've always experienced issues with my card until 3 months ago, when the wireless.kernel.org driver reached a stable state but it looks like they're not anymore.

---

