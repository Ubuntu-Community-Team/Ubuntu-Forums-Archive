---
title: "Problem resizing window for one specific app"
date: 2007-06-18
forum: Desktop Environments
---

### Post by tabithaboof on 2007-06-18
I have been using a piece of software called Cgoban 3 to play an online board game for a couple of years under windows and had it running under Feisty for a a few weeks just fine. You can see the program here 

[http://www.gokgs.com/download.xhtml](http://www.gokgs.com/download.xhtml)

A week ago I started having problems resizing the window. The small window looks like this 

[IMG]http://i54.photobucket.com/albums/g87/dpurdu/temp/Screenshot2.png[/IMG]

but when I click maximise this happens.

[IMG]http://i54.photobucket.com/albums/g87/dpurdu/temp/Screenshot3.png[/IMG]

All my other apps and windows resize perfectly. The only thing I can think of is that I installed Beryl recently but I have tried turning Beryl off but I still have the same issue. Any help much appreciated.

---

### Post by tabithaboof on 2007-06-19
It looks like Beryl was the problem after all, switching back to metacity and I have no problems.

---

### Post by LordKelvan on 2007-06-21
Hi:

I am not sure if this applies to your problem, but there are currently problems between Java-based programs and Beryl (one of them being incorrect re-drawing when maximizing Java apps).  If your app is a Java one, you might try searching with the terms "Java Swing Beryl problems" (or something similar) using Google or going to the new Compiz Fusion forums.

Actually, just as a quick test (if your app is actually a Java one), open up a terminal, and type in the following command:

export AWT_TOOLKIT=MToolkit

Then restart your app and see if that helps at all.

Cheers,
LK

---

### Post by limitedmage on 2007-06-29
I searched the Beryl wiki and found a way to supposedly fix beryl/java problems, but it didn't work. The problem with Cgoban 3 seems to ONLY  be about resizing when beryl is enabled. Anyone managed to fix this?

---

### Post by ukeewu on 2007-07-09
i am having the same problem....but this is a fresh feisty install

no beryl to blame it on here

please help if you know what could be causing this

---

### Post by LordKelvan on 2007-07-12
limitedmage: did you try my suggestion of using export AWT_TOOLKIT = MToolkit?

---

### Post by audiofreq on 2007-12-19
That worked for me but how do i make it permanent?

---

### Post by LordKelvan on 2008-01-07
You can add the whole command (i.e., "export AWT_TOOLKIT = MToolkit") to a file called environment in the /etc folder.

---

