---
title: "Launchers opening up in the wrong monitor on a DUAL-MONITOR rig"
date: 2008-06-16
forum: Desktop Environments
---

### Post by BassKozz on 2008-06-16
I have a dual monitor (separate X-sessions) setup,
I recently upgraded from Gusty (7.10) to Hardy (8.04), and ever since the upgrade, when ever I open up an application from my desktop on the secondary monitor, it opens the application on the primary monitor. But when I open up an application from the menu bar/ panel (TOP = Applications / Places / System) it will open the application in the appropriate (secondary) monitor.

So why are desktop icons (Launcher's) not opening in the appropriate monitor that they reside in? And how can I fix?
Thanks in advance,
-BassKozz

---

### Post by BassKozz on 2008-06-17
:bump: :confused:

---

### Post by darthmob on 2008-06-26
I have got the same problem here with ubuntu 8.04! some applications open on the primary screen and some on the second and I do not see a pattern in it.

PS: I'm using twinview.

---

### Post by BassKozz on 2008-06-26
> **darthmob said:**
> PS: I'm using twinview.
At least with twinview you can move the applications from one screen to another, correct?
With separate X-Sessions I can't move applications from one monitor to the other :(
Maybe i should look into twinview...

---

### Post by darthmob on 2008-06-29
that's right, you can freely move them between the two monitors!

I stopped searching for a solution and I am trying to get used to it. it is not that severe and like you pointed out possible to move the applications anyway.

---

### Post by BassKozz on 2008-09-19
Ok I finally switched from "Separate X-Sessions" to "TwinView" and I am loving it, but this problem with applications opening up in the wrong monitor still exists (as darthmob mentioned).

I think everything defaults to the Primary monitor, and I have to physically move applications over to the secondary monitor even if I've clicked on the desktop icon in the secondary monitor.  Also now that I am not using "Separate X-Sessions" the panel bars only exist in the primary monitor so I can't run applications from the panel bar in my secondary monitor....Is there a way to have the panels expand across both monitors?

Is there a solution available out there?

Another pain-in-the-ar$e is that I like to watch videos (using VLC) on my secondary monitor, but when I select "Full Screen" from within VLC it automatically defaults the full screen to my primary monitor, even if the VLC window resides in my secondary monitor...  Is there a way around this?
**UPDATE:**p.s. This also happens when I am watching a video in FireFox (i.e. YouTube) and I click to make it full-screen, it opens up the full screen in the other (primary) monitor even if the FireFox window is in the secondary monitor.

---

### Post by BassKozz on 2008-09-25
Now I have another problem; [my monitors won't go to SLEEP when I am using TwinView]("http://ubuntuforums.org/showthread.php?p=5851251#post5851251") 
Yet they went to sleep perfectly fine when I was using separate X-Sessions :confused:

---

### Post by BassKozz on 2008-09-27
> **BassKozz said:**
> Now I have another problem; [my monitors won't go to SLEEP when I am using TwinView]("http://ubuntuforums.org/showthread.php?p=5851251#post5851251") 
Yet they went to sleep perfectly fine when I was using separate X-Sessions :confused:

I posted a bug report about this issue here: [https://bugs.launchpad.net/ubuntu/+bug/275308](https://bugs.launchpad.net/ubuntu/+bug/275308)

Also I found an interesting bug report having to do with launchers opening in the wrong monitor here: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845)

---

### Post by BassKozz on 2008-09-28
> **BassKozz said:**
> Also I found an interesting bug report having to do with launchers opening in the wrong monitor here: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845)

Apparently this issue is fixed in the next release of Ubuntu (8.10): [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845/comments/7](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845/comments/7)

---

### Post by BassKozz on 2008-09-28
> **BassKozz said:**
> I posted a bug report about this issue here: [https://bugs.launchpad.net/ubuntu/+bug/275308](https://bugs.launchpad.net/ubuntu/+bug/275308)

Also filed one at bugzilla: [http://bugzilla.gnome.org/show_bug.cgi?id=554247](http://bugzilla.gnome.org/show_bug.cgi?id=554247)

---

### Post by Halter on 2008-10-05
Launchers open depending on wich display you open them, or better to say were mouse focus is. Simply plug usb stick and you'll see what I mean (just press left mouse button on empty desktop space before). As for panels, just add new panel and drag it were U like :-P .

---

### Post by BassKozz on 2008-10-09
> **Halter said:**
> Launchers open depending on wich display you open them, or better to say were mouse focus is. Simply plug usb stick and you'll see what I mean (just press left mouse button on empty desktop space before). As for panels, just add new panel and drag it were U like :-P .

This is not the case, If I click on the firefox icon in my panel that is on my right (secondary) monitor, firefox still opens up on the left (primary) monitor.
This is a known bug and apparently has been fixed in Ubuntu 8.10: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845/comments/7](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845/comments/7)

---

### Post by godz on 2008-11-03
Just installed 8.10 and have this problem. Dual monitors using separate X servers. When I launch firefox, nautilus, etc on my right (secondary) monitor it pops up on the left (primary) screen! Extremely frustrating as I am using the second monitor in a different room for movies. This was working correctly in 7.10. 

Heard something about this problem being solved in 8.10 and Gnome 2.24, but that doesn't seem to be correct. At least nu for dual X servers, I have not tried twinview.

---

### Post by BassKozz on 2008-11-04
Yup, I can confirm... Still broken in Intrepid Ibex (8.10) :(
[Updated on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/224845/comments/12")

---

### Post by burquedout on 2008-12-01
I was having the same problem and I fixed it by deleting my gnome-panel on the second monitor and starting a new panel.  I think the panel was somehow setup for the first monitor so everything opened through it would go to the first monitor.

---

