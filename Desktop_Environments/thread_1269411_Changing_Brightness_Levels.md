---
title: "Changing Brightness Levels"
date: 2009-09-18
forum: Desktop Environments
---

### Post by kkrishnan on 2009-09-18
I have a laptop on which the Fn key doesn't work.  Therefore, I can't reduce the brightness since the hotkey to do that is [Fn key] + [Home/End] on IBM T43s.  I read that there's a brightness applet that can change these settings but have no idea how to find it :-0

Any ideas?

---

### Post by kivanov1992 on 2009-09-18
Sorry, I'm not a specialist, but I'll try to help.
First, the brightness applet (if you use Gnome) can be found easily:
right-click at the free space on the panel, select "Add to panel" (or "Add applet", I don't know how it is in English version). Then, in window appeared choose that applet (you may type "brightness" in search bar at the top of that window).

---

### Post by Shujah on 2009-09-18
Right click on panel and select 'add to panel' there is a Brightness applet available here.

---

### Post by kkrishnan on 2009-09-18
> **Shujah said:**
> Right click on panel and select 'add to panel' there is a Brightness applet available here.

Thanks.  I did that and now there's an even stranger problem.  As I move the slider on the brightness applet, nothing's happening.  Now what?

---

### Post by Shujah on 2009-09-18
Appears to be a bug > [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/134756](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/134756) This page has some workarounds too, check the last couple of posts.

---

### Post by kkrishnan on 2009-09-18
> **Shujah said:**
> Appears to be a bug > [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/134756](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/134756) This page has some workarounds too, check the last couple of posts.

Neither of the workarounds seem to work on the latest version of Ubuntu.  Post no. 10 says to either change an entry in `/etc/modprobe.d/thinkpad_acpi.modprobe', which doesn't exist on my machine or to change an entry in `etc\modules' which exists but doesn't have the line that needs to be changed.

Ergo, no workaround possible :(

---

