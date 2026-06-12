---
title: "Internet Browsers and Ubuntu"
date: 2009-06-18
forum: General Help
---

### Post by Dr Belka on 2009-06-18
Alright guys, I am at a loss here.  I am having some major trouble with the performance of internet browsers in ubuntu.  I have always had problems with memory use and retention in firefox and I tried the "peacekeeper browser benchmark" thing and scored only a 500 in both firefox and opera, which is terrible.  I also have problems with the flash player in firefox.  When ever I am trying to play some stupid internet games it is dreadfully slow.  

I was wondering if it was just my system being slow... So I booted up xp and I had none of these problems.  The browser benchmark for google chrome under xp ranks up high, as it should.  

Then I started wondering if it had something to do with my graphics configuration.  The graphics have always been touchy.  I have and NVidia geforce4 MX 64MB.  I use the "NVidia accelerated graphics driver version 96" which was auto-detected by the hardware drivers manager.  I did try install the "NVIDIA-Linux-x86-96.43.11-pkg1.run" driver for my card, but that always fails miserably...

any ideas guys?

---

### Post by jonobr on 2009-06-18
Hello


I had the ability to do some side by side comparisons of browsers on my jaunty and intrepid systems.

I just got really fed up with FF.

I had one application in particular where there seemed to be an awfully slow response time when working with it and used that application as a bench mark to compare other browsers.

I tried FF and swiftweasel and found them the same with no major differences, you would expect that.

Then I did Opera and epiphany against FF, and both were definately better against my application then FF, I did think that Epiphany was better then Opera.

Finally I tested seamonkey and I believed seamoney had the best performance of the lot, but that iss just me.

---

### Post by lovinglinux on 2009-06-18
You could try these:

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)
[http://ubuntuforums.org/showthread.php?t=1146943](http://ubuntuforums.org/showthread.php?t=1146943)

I have increased Firefox performance by almost 200% with those tips, but I still get less points than you on Peacekeeper.

---

### Post by Dr Belka on 2009-06-19
> **lovinglinux said:**
> You could try these:

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)
[http://ubuntuforums.org/showthread.php?t=1146943](http://ubuntuforums.org/showthread.php?t=1146943)

I have increased Firefox performance by almost 200% with those tips, but I still get less points than you on Peacekeeper.


This is so wierd, but, When I did this, my peacekeeper score fell down 20% and flash is slow as ever.  I am starting to think that SOME of the problem may be my video driver.  I have and NVidia geforce4 MX 64MB. I use the "NVidia accelerated graphics driver version 96" which was auto-detected by the hardware drivers manager. I did try install the "NVIDIA-Linux-x86-96.43.11-pkg1.run" driver for my card, but that always fails miserably...

I tried logging into a terminal only thing, but I dont think I really know how to properly do that.  I booted with the system recovery option in GRUB and found a terminal from there.  Then I get runlevel problems and blah blah blah

---

### Post by lovinglinux on 2009-06-19
> **Dr Belka said:**
> This is so wierd, but, When I did this, my peacekeeper score fell down 20% and flash is slow as ever.  I am starting to think that SOME of the problem may be my video driver.  I have and NVidia geforce4 MX 64MB. I use the "NVidia accelerated graphics driver version 96" which was auto-detected by the hardware drivers manager. I did try install the "NVIDIA-Linux-x86-96.43.11-pkg1.run" driver for my card, but that always fails miserably...

It doesn't work well for you probably because the MX cards are kind of old and don't support the most recent features. I'm just guessing tho.

---

### Post by Dr Belka on 2009-06-19
yeah, ha ha, it happens to be ULTRA-LEGACY HARDWARE!!!!

so yeah, maybe that is my problem....

oh well, thank you for the help : )

---

### Post by lovinglinux on 2009-06-20
> **Dr Belka said:**
> yeah, ha ha, it happens to be ULTRA-LEGACY HARDWARE!!!!

so yeah, maybe that is my problem....

oh well, thank you for the help : )

No need to be sarcastic. I'm just trying to help. I'm saying this because I had a Geforce MX  in the past. It was not very powerful and couldn't render pixel shader, which prevented me from running several modern games.

I'm just saying that the extra options introduced in the xorg.conf file could not work with this particular card model, not because it is not ULTRA-LEGACY HARDWARE, but because they might not be available for that card.

---

### Post by DeMus on 2009-06-20
> **lovinglinux said:**
> You could try these:

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)
[http://ubuntuforums.org/showthread.php?t=1146943](http://ubuntuforums.org/showthread.php?t=1146943)

I have increased Firefox performance by almost 200% with those tips, but I still get less points than you on Peacekeeper.

How do you mean: less point on Peacekeeper?
What is Peacekeeper and what can I do with it?

Nevermind. My friend Google found it.

---

