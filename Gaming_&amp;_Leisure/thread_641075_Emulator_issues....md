---
title: "Emulator issues..."
date: 2007-12-15
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2007-12-15
Hello all! I installed Zsnes from the repos around 2 days ago. It worked perfectly with no problems, as usual I set it to start in full screen mode. The problem is that after the first day of playing and all that it stopped working, I just click on zsnes on the games section and it tries to open and go into full screen but it goes back to desktop instantly without giving me any error message, it's like a flash, no more than a second. The other emulator issue I have is Mupen64 which is a Nintendo 64 emulator. I also got that one from the repos and it opens perfectly always but when I try to play a rom the program closes itself instantly and it also doesn't give any error message...you know, at least I want to know what caused that! I thought it could be a graphics card/driver issue but I'm running Beryl right now without any issues as I type!!!

---

### Post by Dimitriid on 2007-12-15
Try turning off Beryl.

Also type zsnes on a terminal to see what error message you get since its closing right away.

---

### Post by Moonfrost on 2007-12-15
> **Dimitriid said:**
> Try turning off Beryl.

Also type zsnes on a terminal to see what error message you get since its closing right away.

I'll try that, thanks!

---

### Post by acoustibop on 2007-12-15
Mupen64 isn't in the repositories, Moonfrost.  And for ZSNES, Dimitriid's suggestions are the best way to go.

---

### Post by Moonfrost on 2007-12-15
> **acoustibop said:**
> Mupen64 isn't in the repositories, Moonfrost.  And for ZSNES, Dimitriid's suggestions are the best way to go.

Check for yourself, I downloaded it twice already and it works but doesn't launch games...

Anyway, thanks for your help, I'll try turning off Beryl then and see what happens...

---

### Post by acoustibop on 2007-12-15
It most certainly isn't in any of the Gutsy repositories, Moonfrost.  Perhaps you've enabled some specialist repository that includes it?

Otherwise, you're not thinking of Mednafen, are you?  That's a completely different emulator.

---

### Post by yipeskop on 2007-12-15
I'm having the same problem with the pcsx emulator, I turned off Beryl but it still wont work.

---

### Post by FranMichaels on 2007-12-15
> **Moonfrost said:**
> Check for yourself, I downloaded it twice already and it works but doesn't launch games...

Anyway, thanks for your help, I'll try turning off Beryl then and see what happens...

Mupen64 *is not* in the official Ubuntu repositories.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Search for yourself.

If you've added a 3rd party repository, that is another story.

With that out of the way, how about the text when zsnes is run from terminal?

If you see an error regarding *mcop*, check my [how-to]("http://ubuntuforums.org/showthread.php?p=3694819").

---

### Post by FranMichaels on 2007-12-15
> **yipeskop said:**
> I'm having the same problem with the pcsx emulator, I turned off Beryl but it still wont work.

You may want to open your own thread. I can tell you that pcsx does run fine with compiz-fusion enabled. Try a different graphics plugin, or launch *pcsx* from terminal, to see it shows any useful error messages. :)

---

### Post by Moonfrost on 2007-12-15
> **acoustibop said:**
> It most certainly isn't in any of the Gutsy repositories, Moonfrost.  Perhaps you've enabled some specialist repository that includes it?

Otherwise, you're not thinking of Mednafen, are you?  That's a completely different emulator.

Trust me, I know what Zsnes is...I'm an emulation (specially SNES enthusiast)...might be because I'm using Ubuntu Ultimate Edition...I don't know...

---

### Post by FranMichaels on 2007-12-15
> **Moonfrost said:**
> Trust me, I know what Zsnes is...I'm an emulation (specially SNES enthusiast)...might be because I'm using Ubuntu Ultimate Edition...I don't know...

I think acoustibop meant mupen64. zsnes has been in the repos since the first ubuntu release. :)

See my post above if that matches your zsnes error. I was just using it a little while ago. My favorite emulator without question.

---

### Post by acoustibop on 2007-12-16
Exactly so, FranMichaels.  My first statement in this thread was "Mupen64 isn't in the repositories, Moonfrost," in response to his original post, which included "The other emulator issue I have is Mupen64 which is a Nintendo 64 emulator. I also got that one from the repos..."

I think Moonfrost must be a little confused. ;)

---

### Post by Moonfrost on 2007-12-16
> **acoustibop said:**
> Exactly so, FranMichaels.  My first statement in this thread was "Mupen64 isn't in the repositories, Moonfrost," in response to his original post, which included "The other emulator issue I have is Mupen64 which is a Nintendo 64 emulator. I also got that one from the repos..."

I think Moonfrost must be a little confused. ;)

Haha so sorry about that! anyway, I re-installed zsnes, turned off beryl and compiz and still will flash like it's going to open and then it closes itself without any error message...will check running from a terminal window to see what happens...

---

### Post by Chaz_UK on 2007-12-16
I think I'm having the same problem.

```
charles@Core2Duo:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/charles/.kde/socket-Core2Duo.
can't create mcop directory

```
Any ideas?

---

### Post by acoustibop on 2007-12-16
There are several threads here on this with fixes, Chaz_UK - just search on "mcop directory."

---

