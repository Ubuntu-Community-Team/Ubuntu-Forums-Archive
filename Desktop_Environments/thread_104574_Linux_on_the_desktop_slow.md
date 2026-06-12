---
title: "Linux on the desktop slow?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by toon on 2005-12-16
Hello,

So after using Ubuntu for a while, I have to say I'm pretty dissapointed in the performance, and here's a few reasons why:

[LIST]
[*]amarok will always use from 2-5% or my CPU. At trackchanges this skyrockets to 20-30%
[*]xorg uses way more than I think it should be
[*]all the applications generally feels slow, especially when I'm switching between them (in osx it's instantaneous)
[*]same thing with changing desktops
[*]flashmovies etc embedded in a browser makes it take anywhere from 10 to 80% CPU-time
[*]last but not least, just moving a window around makes xorg use about all the CPU there is, and if I move a windows around long enough, it will cause my loadaverage to go to 1-3!!
[/list]

This isn't a comprehensive list by any means, but you'd think these things should go blistering on a 3.2ghz with a Radeon x600 256mb with 2gb ram and glx enabled. What, so I can't except to move a window without it taking 3.2ghz to compute?

I've tried this both with and without Renderaccel. glxinfo sais I have direct rendering. fglrx_gears confirms this (get around 2000 FPS).

Is this just how it works because of Xorg/bad drivers? If it it, I might well move back to OSX or even Windows, where the responsiveness thwarts my current system..

I realize this is more related to GNU/Linux than Ubuntu. As a server linux is very good, but this is pretty annoying..

Any suggestions? Or is this just how it is?

Thank you for your time.

---

### Post by aysiu on 2005-12-16
[QUOTE=toon]
This isn't a comprehensive list by any means, but you'd think these things should go blistering on a 3.2ghz with a Radeon x600 256mb with 2gb ram and glx enabled. What, so I can't except to move a window without it taking 3.2ghz to compute?[/QUOTE] They go blistering on my 512 MB of RAM. I don't know why they wouldn't on 2 GB of RAM.

But then again I don't know why Mac OS X is so sluggish on my wife's Powerbook that has 1 GB of RAM, either.

---

### Post by Hairy_Palms on 2005-12-16
well for the poor xorg performance and changing desktop, id blame the poor drivers from ati rather than linux, ive never met a pc with an ati card that didnt use stupid ram amounts because of crappy drivers.

---

### Post by Mustard on 2005-12-16
Toon, what brand of cpu are you using, and what kernel are you running?

---

### Post by toon on 2005-12-16
[QUOTE=Hairy_Palms]well for the poor xorg performance and changing desktop, id blame the poor drivers from ati rather than linux, ive never met a pc with an ati card that didnt use stupid ram amounts because of crappy drivers.[/QUOTE]
Right, this is really my conclusion from reading around as well. It seems resonable then to suggest Linux as a vital alternative for regular users only to those with nvidia. Because even though this *works*, it's works unresonably slow.

And I wasn't blaming anyone..

---

### Post by KermitJr on 2005-12-16
Two questions.

1) Would you rather take all 3.2GHz and do the job faster or run slower and take longer?  I prefer that full force be used to get a task done, no matter how small the task.  Note: I'm not saying it SHOULD take that much that long, but if it will take, say, 64 of something, I'd rather through 2x32 at it than 4x16.

2) Have you tried getting a specific kernel vice the i386?  In Mac, the kernel is optimized for the processor... that's the advantage of closed hardware.  In linux, it has to be able to run on many combinations.  Try apt-getting a faster kernel, and if that doesn't work, roll your own.  I noticed a bit difference between i386 and i686 with regards to responsiveness.

KJ

---

### Post by toon on 2005-12-16
[QUOTE=Mustard]Toon, what brand of cpu are you using, and what kernel are you running?[/QUOTE]
It's an Intel P4 3.2 GHz. 

uname -a gives: "Linux Phobos 2.6.12-9-686-smp #1 SMP Mon Oct 10 13:36:57 BST 2005 i686 GNU/Linux"

I've not done anything on the computer since the last post, and the loadaverage resides steadily at 0.4, which seems really high given the activity..

---

### Post by linbetwin on 2005-12-16
I have an ATI RADEON 7000 VE card and I don't have those problems. And I'm using the drivers that came with Ubuntu.

---

### Post by toon on 2005-12-16
[QUOTE=KermitJr]Two questions.

1) Would you rather take all 3.2GHz and do the job faster or run slower and take longer?  I prefer that full force be used to get a task done, no matter how small the task.  Note: I'm not saying it SHOULD take that much that long, but if it will take, say, 64 of something, I'd rather through 2x32 at it than 4x16.
[/QUOTE]
I'd just don't see how you can justify using 3.2ghz for repainting the desktop. Other things will be affected (proven by the increased loadaverage).
[QUOTE=KermitJr]
2) Have you tried getting a specific kernel vice the i386?  In Mac, the kernel is optimized for the processor... that's the advantage of closed hardware.  In linux, it has to be able to run on many combinations.  Try apt-getting a faster kernel, and if that doesn't work, roll your own.  I noticed a bit difference between i386 and i686 with regards to responsiveness.
[/QUOTE]
I hear this from time to time, but this seems like a moot point for me; generally, these optimizations give a small linear performance boots. I don't see how going from my 686-smp to a custom one will reduce the repainting cost from 80% to 1%, unless my Ubuntu-kernel has serious incompabilities with my regular P4 cpu..

---

### Post by toon on 2005-12-16
[QUOTE=linbetwin]I have an ATI RADEON 7000 VE card and I don't have those problems. And I'm using the drivers that came with Ubuntu.[/QUOTE]
Could you try moving a window around for 10-30 seconds and watch top as you do it? X is hit really hard on my setup, resulting in high loadaverages.

---

### Post by greenwom on 2005-12-16
I would do as sujested and install the i686 kernel.  From what I've read it's seems to be the best fit.

---

### Post by toon on 2005-12-16
[QUOTE=greenwom]I would do as sujested and install the i686 kernel.  From what I've read it's seems to be the best fit.[/QUOTE]
As you can see in the thread, I'm using the i686-smp. I've tried the regular as well, by the way.

---

### Post by angkor on 2005-12-16
I've seen quite a few of these threads, yet I can honestly say I've never experienced slowness on my box (Sempron 2800+, 1GB ram, ancient nvidia card).

Xorg does take a lot of mem and cpu but it doesn't result in any slowness. Switching apps and workspaces is instant, yet I do see increased cpu usage when resizing and moving windows. I've disabled renderaccel cause it tends to crash X on my box. 

I understand this isnt very helpful but it could be ubuntu is having trouble with your hardware, cause on mine it runs very fast considering the hardware.

---

