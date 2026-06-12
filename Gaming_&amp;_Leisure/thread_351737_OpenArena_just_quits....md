---
title: "OpenArena just quits..."
date: 2007-02-02
forum: Gaming &amp; Leisure
---

### Post by tocleora on 2007-02-02
I'll be playing OpenArena and it will just quit at random points.  Can be within a minute of playing, can be within a couple of hours of playing.  Anyone experienced anything similar and if so is there a fix?  TIA...

---

### Post by conjur3r on 2007-02-03
Try running the game from a terminal and next time it crashes, it *should* dump some information for you which might help you pinpoint the problem.  I'm not sure if this method will work as I haven't played it before.

---

### Post by tocleora on 2007-02-03
Cool, I'll try that. thanks.

---

### Post by tocleora on 2007-02-04
alright, here's the results:

```

ioquake3.i386: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Received signal 6, exiting...
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Shutdown tty console

```

Anyone familiar with this error?

---

### Post by conjur3r on 2007-02-05
Are you running an intel graphics card?  Also, do you have XGL running?

As a test, try leaving the following running for a couple of minutes to see if it crashes abrubtly or not.

# glxgears -printfps 

If it crashes out, you may have an issue with your drivers.

---

### Post by tocleora on 2007-02-05
Yes, I believe it's an Intel 915GM if I remember correctly.

No, I don't have XGL running.

glxgears -printfps didn't work (printfps is apparently not an option under my version), so running glxgears I ran it for at least 30 minutes without it crashing.  It *did* show me fps averaging 500-800 for the most part with a few dips to 300.  

However... When I do run XGL and Beryl, Beryl does something similar, crashes a lot... returns to a login prompt for a few seconds then returns to the gdm login where I can log back in and restart beryl-manager.  Does that help?

---

### Post by conjur3r on 2007-02-06
Sounds like you may have an issue with your display drivers, either the intel drivers, dri, or even mesa...  Maybe reinstall them but I'm not sure if this will fix it.

I did a quick google search for [hHWContext]("http://www.google.com.au/search?q=hHWContext+failed&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a") and it looks like many others are having similar issues.

Sorry, that's all I know.  Couldn't find an answer :(

---

### Post by tocleora on 2007-02-06
Thanks anyway, I'll hopefully be upgrading soon, I have the option of getting my boss's laptop which has an ATI graphics card in it, or I've been throwing around the idea of building a small computer I can carry back and forth and putting an nvidia card in it.  I'll just wait it out until then. :)

---

### Post by conjur3r on 2007-02-07
Before you commit to the laptop, make sure you read up on the vast issues people are having with the ATI drivers and also make sure that the wireless card works (preferably without using ndiswrapper as some modes and functions do noot work with ndiswrapper).

For what it's worth, I'd recommend a nvidia card and either an intel or an atheros chipset wireless card.  They should work with the least amount of difficulty.

---

### Post by tocleora on 2007-02-07
If I get the laptop, it won't be by choice. ;)  It's an upgraded version of the same one I have so I'm going to guess the wireless card is the same as mine, however it does have the ATI card in it and yes from reading about video cards I've seen that nvidia seems to be the absolute best way to go.  Even if I do get the laptop if it doesn't work any better I'll still build the other computer and put an nvidia in it because I just have to see Beryl and OpenGL Games work well on Ubuntu! :)

---

