---
title: "Framerate issues with AMD &amp; Intel graphics"
date: 2014-02-04
forum: Gaming &amp; Leisure
---

### Post by Ranko Kohime on 2014-02-04
I have the proprietary AMD Catalyst drivers installed in Linux Mint 15, (analogous to Ubuntu 13.04 Raring), and I'm having a very weird issue.

I have both an HD 7850, and an R9-290, running on an A8-6600K APU.  I've tested with both cards in, just the 7850, and just the 290, and even with just the APU, but I consistently get the same issues.

A Source-engine game gives me quantifiable results, as it has a frame counter I can enable.  With Tear-free DISABLED in the CCC, and with vsync either enabled or disabled in game (it has no effect either way), my frame rates go from 60, down to the teens, and up into the 180's, VERY rapidfire.  Naturally, I'm getting screen tearing AND more input lag than I would expect from the framerates being in the teens.  I've removed the proprietary drivers and reinstalled, tried the Beta drivers, stable drivers, everything, and they all do the same thing.  This happens on ALL games.

Google doesn't seem to want to assist me with this specific issue, so perhaps someone here has a clue as to what is going on?

---

### Post by dannyboy79 on 2014-02-07
may i suggest trying to newer kernel, like 3.13 and then using Oibaf's PPA for the latest radeonsi drivers. They should prove to be much more stable then fglrx

---

### Post by Ranko Kohime on 2014-02-27
Ok, I'm going to open this up a bit.  The same behavior, (framerates wildly varying even under V-sync) occurs on my Intel laptop as well, which is now running Manjaro 0.8.9.  I'd like to get other people's experiences to see if this issue is deeper than just the AMD drivers.

Just to clear this up: Previously, nearer to 12.04, (I never ran Steam on 12.04, but I think I did on 12.10), my Intel laptop would have graphic performance similar to Windows, where the framerates would vary in a tight range if just looking at a wall, and would rise or fall depending on the scenery in the current frame.  The behavior now is that the frame rate varies wildly, including impossible framerates of almost 200 on my Sandy Bridge graphics, all the way down to stutter-inducing single-digits, just standing still looking at a wall.

---

### Post by Jake_Paine on 2014-03-04
I'm having a similar issues but with a different setup - [http://ubuntuforums.org/showthread.php?t=2208941](http://ubuntuforums.org/showthread.php?t=2208941)

Crossfire is now working (or registered as working) but performance has not increased as is way lower than what it should be. Have you tried any different drivers yet or just the AMD ones?

---

### Post by xinghua31 on 2014-03-07
I think I'm having this issue too. How do I get an FPS counter in L4D2?

---

### Post by Jake_Paine on 2014-03-07
Apparently the ` key should bring up the console but evern after adding it into my cfg it's not working. Without getting the console open you can't display the FPS. Maybe you will have more luck.

Sources:

[http://www.gamefaqs.com/boards/960510-left-4-dead-2/52639319](http://www.gamefaqs.com/boards/960510-left-4-dead-2/52639319)
[http://www.esl.eu/eu/l4d2/forum/2049/16972/710094/?lastvisit](http://www.esl.eu/eu/l4d2/forum/2049/16972/710094/?lastvisit)

---

### Post by xinghua31 on 2014-03-07
The console is not working for me either.

---

