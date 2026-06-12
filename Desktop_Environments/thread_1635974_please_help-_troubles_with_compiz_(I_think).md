---
title: "please help- troubles with compiz (I think)"
date: 2010-12-02
forum: Desktop Environments
---

### Post by zvi on 2010-12-02
Ive been running an emerald therme in compiz for z few months now and everything was running fine when a couple days ago VLC started acting weird and playing little staticky clicks avrery few seconds.

Then the next time I booted up after an initial second of flashing my full desktop the screen blanked off a section on the left and bottom of my screen. When I logged in docky told me it was having trouble with the compositing, but when I scrolled over the spot where my docks are they were there. My arrow can be seen in the black areas as can the start panel when I scroll over it, but aside from that it is black and when I open I window the blackness covers it in that part. None of my compiz effects seem to be working.

I am running a pretty basic motherboard and I know basically nothing about this kind of thing but I looked up the built in integrated video card online : ATI Radeon™ HD3000 Graphics, On Board Graphic Max. Memory Share Up to 512 MB.

I have an ATI driver installed but when I look at my drivers it says it is installed but not currently in use. When I look at my visual effects page it is on none, so I tried changing it to normal and it says the effects can't be enabled.

I am running a dual boot with windows and when I go into windows there doesn't seem to be any problems.



I am running a Biostar A760G M2+, an AMD AthlonII x4 and running Ubuntu 10.04

Any help figuring this out would be greratly appreaciated,

Zvi

---

### Post by gogolink on 2010-12-02
One tool that I have found useful in dealing with Compiz is a script called **compiz-check** (which you can find here (Thanks, Forlong!): [http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")).

Perhaps you can run the script and post the output?

---

### Post by zvi on 2010-12-02
Thanks. I ran that and it says I have no rendering method.
I don't know what to do about that (or what it means actually)

I am attaching the resulting terminal screenshot.

---

### Post by zvi on 2010-12-02
IM goign to try removing the driver and then reinstalling it. Could that help at all?

---

### Post by zvi on 2010-12-02
Well, I reinstalled the driver and then needed to restart the computer. After doing so compiz still wasnt working, but then I reloaded the windows manager through the compiz fusion icon and its working again.

Thank you gogolink.

---

### Post by gogolink on 2010-12-02
There seem to have been some problems with ATI graphics cards and Compiz.  I don't have ATI, but came across this post: [http://ubuntuforums.org/showthread.php?t=1362818]("http://ubuntuforums.org/showthread.php?t=1362818"), which could be interesting for you.  For some of the posters, running the command **aticonfig** solved the problem (proposed by ashokmkd in post #14).

Oh sorry, I see your problem is solved...  So you can disregard this last post (:

---

### Post by zvi on 2010-12-02
Actually, I just rebooted again and it seems my computer is still somehow starting up without running compiz properly and then I continually need to reload the windows manager. So its somewhat fixed, but not completely. I think Ill try your suggestion.

---

### Post by zvi on 2010-12-02
Hmm, I looked at that post. and tried doing compi-check again andf it is still telling me that there is no rendering method, even though I am using compiz while doing the test.

also I tried the Anticonfig and it keeps telling me "command not found"

---

### Post by gogolink on 2010-12-02
You did type "**ati**config" in your terminal, didn't you -- not "**anti**config" (as you write in your post)?  Just checking.

---

### Post by zvi on 2010-12-03
oh, wow, I cant believe I made that mistake. Well it worked when I wrote it properly.

IM not sure yet if it helped at all though.

---

### Post by Julitokenpo on 2011-04-03
Have you tried compiz-replace ????? It worked for me.....

---

