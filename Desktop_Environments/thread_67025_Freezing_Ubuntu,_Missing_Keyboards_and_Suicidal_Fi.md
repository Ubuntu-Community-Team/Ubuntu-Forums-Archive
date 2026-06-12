---
title: "Freezing Ubuntu, Missing Keyboards and Suicidal Firefox"
date: 2005-09-19
forum: Desktop Environments
---

### Post by TheGrza on 2005-09-19
The joys of writing message board posts about problems, post that are interrupted in the middle by the problems themselves.

Alright, I'm having several issues, all of which started at the same time.  I recently moved a few thousand miles and after unpacking my computer found that when I used GSnes9x for a period of time around 45-60 minutes Ubuntu would irrevocably freeze.  I would then restart the computer which said that it couldn't then find my keyboard or mouse.  Thinking that my keyboard connections had been fouled up in the move, I took it apart, taped up some wires and put it back together.  This failed to solve the problem, so I avoided GSnes9x.  I found, strangely, that after shutting down and letting the computer sit for about 10 minutes I could start it back up and it would find everything.

I began to watch some .avi files on Totem Movie Player, moderately sized resolution files, that would run for a while and then freeze, same as with GSnes9x.  Lower resolution files would run for hours with little problem.  This has gotten worse lately until higher resolution files get about a minute before freezing and lower resolution
files get about 10 minutes.

The only other time it has happened is listening to .mp3 files using XMMS and running Firefox with several tabs open, usually to RAM sucking webpages.

After recognizing this, I began to run System Monitor in the background to try to catch one of these freezes in action and figure out where my system was breaking down and if it was the large % of CPU or Memory involved that was doing it.  Several times I caught the freeze only to find that the CPU% was somewhere at a steady 30-40%, depending on the programs in use at the time, with User Memory at about 50% and Swap at around 4-8%.

While cooking one night, the problem arose and I let the computer start all the way  up after it didn't find the keyboard or mouse.  At this point everything was normal and the keyboard and mouse had evidently been recognized, but the problems with freezing still remained.   My Ubuntu Mentor and Dumpster Diving Parts Man told me he thought it was a faulty stick of RAM he had scavenged for me, and suggest I run memtest at the startup of my computer.  Several restarts and a pounded ESC button led to nothing; the computer never recognized my attempts in the least.  Following on his train of thought, I removed the sticks of RAM (individually) and found that my computer ran the same (albeit slower) way that it had before, freezing and then failing to find the keyboard and mouse while finding them all the same.

Other problems which started up at the same time include:
*Clicking - There is a pretty severe clicking noise when starting up initially or giving me my "No Keyboard" message"
*Beeping from the Machine - I don't remember what the computer beeping in various pitches means, it's just been too long since it happened, but it's happening now.
*Crashing of Firefox - Firefox has simply been quitting itself, blinking out of existence with no explanation or apology, and no "Do you want to restart this failed application".  Never happened before.


I think I've ruled out simple moving as the impetus for these problems.  All connections have been checked and rechecked, pulled out and stuck back in in an attempt to find something not hooked up right.  I'm bewildered as to whether this is even hardware or software with the beeps and the clicks and the spontaneously combusting Firefox.  I need some help, if only a direction to continue testing hypothesis, of which I am currently out.

---

### Post by TheGrza on 2005-09-20
Update and Third Plea for Help:

Making the assumption that it was software, I created a new user account to find that the same crashes were happening.  It also continued to happen with GSnes9x.  I would have it narrowed down to the various codecs I have installed, except for the GSnes9x crashes.  Does anyone know if the multimedia codecs have any bearing on GSnes9x?  If not, any advice on the larger issue?  Sorry it's so long by the way, but I'm in serious need of help.

---

### Post by haplo770 on 2005-09-20
I am not an Ubuntu user but what you are describing may be a cpu issue. I once had a system that the cpu fan was not correcly installed and the system would work for a while and then crash, this happened while playing video games or while watching a movie (in windows), it would also crash while trying to compile a kernel in linux. This was a AMD xp  cpu and the temperature was about 58 deg. C after properly reseating the fan (clean an replace the thermal compound) the temp dropped over 20 deg. C.

If your motherboard has a temperature sensor check it out in the bios.

This may be your problem. let me know

---

### Post by bob k on 2005-09-20
The clicking sound is usually related to a disk drive going bad.

---

### Post by crispingatiesa on 2005-09-20
It sounds like a hardware induced failure. I would go by:

Checking CPU temp+ fan first.

Reset the BIOS parameters as safe as possible (increasing memory latency times etc.., ussually BIOS have different presets like Turbo, Optimal, Safe etc,)

Check the HD some BIOSes have this option to test for an about to fail HD

Check for some semi-loose cards.

Note: the beeping sound means different things for different motherboards and is based in a code that should be printed in the mobo mannual. if you have it check it otherwise go to the mobo manugactrue webpage and download the manual

---

### Post by ygarl on 2005-09-21
[QUOTE=crispingatiesa]It sounds like a hardware induced failure. I would go by:

Checking CPU temp+ fan first.

Reset the BIOS parameters as safe as possible (increasing memory latency times etc.., ussually BIOS have different presets like Turbo, Optimal, Safe etc,)

Check the HD some BIOSes have this option to test for an about to fail HD

Check for some semi-loose cards.

Note: the beeping sound means different things for different motherboards and is based in a code that should be printed in the mobo mannual. if you have it check it otherwise go to the mobo manugactrue webpage and download the manual[/QUOTE]
 Deffo a hardware prob - sounds like overheating to me.
I had a (Win XP) PC which had some serious overheating probs due to a lack of air supply fromt he back of the PC which would start acting wierd for no apparent reason in warm weather  or whenever I left it on for more than about 45 mins or so.

Moved the PC, and took one side off (the side facing a file cabinet less than a inch away) and all was well...

---

