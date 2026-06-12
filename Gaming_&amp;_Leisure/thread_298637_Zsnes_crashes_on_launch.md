---
title: "Zsnes crashes on launch"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by Mimsy on 2006-11-13
Hi!

I have another problem with Zsnes.

Basically, it works about 50%of the time. The remaining 50% it crashes on launch. The whole screen (I run it in full-screen mode) turns into what can only be described as a checker board designed by Picasso during a hang-over. The white and black little squares sit absolutely still, there's no sound, no movement, and I can't get the laptop to react to anything except for the powerbutton. So I press that, and the laptop reboots. (I have had to do this a lot, and I am concerned that it might not be good for my Ubuntu installation.)

So the last time it worked I had the brilliant idea (at least I think it's brilliant) to switch Zsnes to run in windowed mode and see what happened. Nothing, it still worked, so I opened a system monitor next to it, to try and figure out what was going on. I found my problem. The graph showing CPU activity lays consistently at 98-100 percent! I had no other application open at the time. None that I am aware of anyway... 

That CPU load would explain the crashing, I guess.

Now, finally, to my question: Can this be fixed in some way, or should I just move to another emulator and pray that my save files transfer? I would hate to lose those saves, naturally, but if there is no other solution I will mourn them and then move on.

Help will be greatly appreciated!

/Mimsy

---

### Post by po0f on 2006-11-13
Mimsy,

You mentioned that this was on a laptop.  Does it have a dedicated 3d graphics card, or is it one of those integrated jobs?  The integrated graphics (if you have them) explains the 100% CPU usage.  

zsnes is chugging along just fine on my desktop at 6.5%.  OTOH, I did get zsnes to work on my T22 (with a Savage graphics chip), but CPU usage was kinda high;  I didn't experience the crashes you are though.

Please post the CPU and GPU on this system, then we can work it out from there.

---

### Post by Mimsy on 2006-11-13
It's integrated graphics, on a Compaq Evo N410c. I can't post detailed specs until I'm at home with the actual laptop though, which will be in about 24 hours or so. I'll be home before then, but a horrible evil called Term Paper will be keeping me busy. :(

Thanks!

/Mimsy

---

### Post by Mimsy on 2006-11-14
Okay, here we go. According to the Device Manager,this is what I have in the laptop: 

For graphics: Radeon Mobility M6 LY
Processor: Unknown Device.

The laptop was built by Compaq in 2002, and a search of their webpage didn't help at all. I found six different manuals, but none of them say anything about the CPU. The link "parts information" was dead, and the support forum likewise was a blank. But everything else in the laptop is some form of Intel chip, so I would assume the CPU is as well.

/Mimsy

---

### Post by po0f on 2006-11-14
Mimsy,

Read [this](http://h18002.www1.hp.com/products/quickspecs/11375_div/11375_div.HTML) for more info on your lappy.

Well, it's a lot better than mine.  Are you sure that the radeon/ati/fglrx/whatever drivers are working correctly?

(I actually lied about the not crashing on my T22, it does when I change the resolution in the program.  I usually have to edit the config to change it.  Going from full-screen to windowed mode doesn't crash it, however.)

---

### Post by Mimsy on 2006-11-14
That would be the link that was dead when I tried it, I think... I recognise the url. How frustrating.

I have a Intel MobilePentium III 1.2 GHz then.

I haven't done anything to or with the drivers after I went through the whole sudo dpkg-reconfigure xserver-xorg command through the terminal, but setting the integrated grpahics to use ATI drivers didn't change anything;  Zsnes still occasionally crashes. That was a week or so ago, I think, and I ran that hoping that would solve the problem. Sadly, it didn't.

/Mimsy

---

### Post by po0f on 2006-11-14
Mimsy,

As much as I would hate to recommend something other than zsnes, have you tried any other emulators?  Maybe it is a zsnes-specific issue.

---

### Post by Mimsy on 2006-11-14
I have tried other emulators, but not on tis laptop. I'd prefer not to switch, since I have save files I want to keep; that said, I haven't tried to run another to see if the same thing happens with CPU useage. That would be interesting to find out.

/Mimsy

---

### Post by Mimsy on 2006-11-14
Okay, I found out. With Snes9X, installed through Add/Remove since I'm lazy, CPU load is somewhere between 50 and 60 percent the entire time. It must be a Zsnes issue then. Bummer.

At least now I know,  and I'll have to settle for playing new games in Snes9X. With any luck, the issues with Zsnes will be fixed soon.

Thanks for all the help, po0f!

/Mimsy

---

### Post by hikaricore on 2006-11-14
You could try compiling zsnes from the source to see if it makes any difference.  Also if you havn't check to see if direct rendering is enable on your system (from a terminal):

```
glxinfo | grep rendering
```

If this returns a "No" then your computer's processor is doing all the work for the video instead of the graphics card.  At that point if it is a No, then you'll need to lookup how to enable direct rendering.  :)

---

### Post by Mimsy on 2006-11-14
I copy/pasted that command into a terminal, and it said "yes". That means it is enabled, I assume, and therefor I can't change it. Blast!

Ah well, it was worth a try. :)

/Mimsy

---

### Post by CrinkElite on 2007-12-19
I cant get zsnes to load, when i click the icon in games it starts a window but immediately shuts down  i installed it using the spm 
when i try it from the terminal it spits this out:

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/crinkelite/.kde/socket-crinkelite-desktop.
can't create mcop directory
crinkelite@crinkelite-desktop:~$ 


do i have to install KDE, i think its a file manager but i don't know my **** from my elbow here so i'm not sure about any thing.  
Ps. my mouse works perfectly on my desktop (its a usb mouse)

---

### Post by acoustibop on 2007-12-19
Search Games & Leisure on "mcop directory," CrinkElite.  AIR there at least a couple of threads on this including fixes.  Don't bother about the mouse thing and there's no need for you to install KDE (?).

---

