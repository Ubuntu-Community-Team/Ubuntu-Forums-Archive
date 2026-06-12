---
title: "Wubi installs fine, tha freezes during booting"
date: 2009-02-13
forum: General Help
---

### Post by hhall on 2009-02-13
Hi. I am a newbie to this, so please be patient.

I am trying to install Ubuntu through Wubi (both are the newest versions) on a 2008 Fujitsu Siemens Amilo Pi 1530 laptop (2.2 GHz Intel Dual Core, 2046 MB Ram), which is about a year old and so far ran on Vista. I previously tested Ubuntu from the LiveCD; it worked fine (but didn't switch off quite properly).

Wubi installed without difficulty. On rebooting (fisrt boot), I get to choose Ubuntu. Then the booting bar (or whatever it's called) moves right and left for a bit. After that, the bar reappears, and starts up to fill up from the left. It stops and freezes after 3% per or so.

Any idea why this might happen and what I can or should do?

HH

---

### Post by hhall on 2009-02-13
That should read "then", not "tha" in the title.

---

### Post by hhall on 2009-02-13
I assume it doesn't matter, but I mistyped. It's an Amilo 2530, not 1530. 

HH

---

### Post by hhall on 2009-02-14
Actually, it looks identical to [this reported problem (link)]("http://ubuntuforums.org/showthread.php?t=1030172&highlight=wubi+freezes"), as far as I can see, and freezes at the exact same spot. But the solution suggested there doesn't seem to work for me.

---

### Post by hhall on 2009-02-15
Hmmm. I feel a bit lonely here. Does anyone have an idea as to how I might get Wubi/Ubuntu to work? If I need to provide more information, I'd be happy to do so, but as I say, I'm new to this, not very clued in, and do need help.

---

### Post by wakkekrakken on 2009-02-15
Unfortunately, I have the exact same problem. Mine looks some what like your description too.

[IMG]http://i44.tinypic.com/2mchdma.jpg[/IMG]

I've been searching for a fix all over, but I haven't had any luck what so ever yet. I also installed Ubuntu through wubi.

---

### Post by azmo35 on 2009-02-15
Hi,mate have you tryed uninstall and install again, maybe that will help you.

---

### Post by wakkekrakken on 2009-02-15
As for myself, I've tried that several times. I've even tried re-installing from a CD, USB stick and wubi again.. I'm not having any luck though, sadly.

I encounter the same problem each and every time.

---

### Post by hhall on 2009-02-15
Yes, that image is quite like what I get. I have uninstalled and reinstalled several times, to no avail...

---

### Post by azmo35 on 2009-02-15
Well it could be a problem with intel onboard graphics on certain motherboards (845),so this i think is a bug related with compiz.
Boot you pc and press esc"key" on the menu look for Failsafe Terminal Session.
> sudo apt-get remove compiz compiz-core  quit reboot maybe this work.

---

### Post by wakkekrakken on 2009-02-15
Well thanks for the tip azmo35 but I've decided I'm going to give Ubuntu a miss sadly. Sigh.. I just hate it when things don't go as planned lol.

---

### Post by enjoi19 on 2009-02-16
actually when i used wubi, you install, then boot into windows once before, reboot, then select ubuntu

---

### Post by hhall on 2009-02-16
I've tried all that. It always gets stuck at the same point. To be honest, I had hoped that I'd find some help on this forum. I guess that was too much to hope for.

---

