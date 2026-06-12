---
title: "Unity Menu on Two Monitors"
date: 2011-05-01
forum: Desktop Environments
---

### Post by altintx on 2011-05-01
Upgraded laptop to 11.04 last night, and it worked great. Unity was pretty good. But upgraded my dual-monitor desktop earlier today, and realized the laptop's single screen of limited resolution was the reason it was working well. 

On my desktop, Unity is giving me headaches. First, after upgrade, it appeared on the left-edge of the right monitor (IE, it was centered across the width of the screens). Managed to change my primary screen via instructions on [http://ubuntuforums.org/showthread.php?t=1719754](http://ubuntuforums.org/showthread.php?t=1719754) and now it's more sensibly on the left edge of left screen. 

Trouble is, now, I've got 3000-odd pixels between edges. Previously I had a dock along the bottom, and Compiz Scale and Gnome-Do summoned on the screen I was working on. Now everything seems to be so focused on the left screen that the utility of the right screen is severely limited. 

What I'm hoping to learn is
1) Is it possible to put the Unity menu along the bottom of a given screen rather than left of a given screen? (Mac/Windows/KDE-style docks)
2) Is it possible to have 2 unity menus, one on left-side-of-left and the other on right-side-of-right?
3) Any other strategies for working with multiple monitors in Unity?

Not really interested in being the Luddite sticking with Ubuntu Classic if it can be helped. Really like global menus (and mirrored global menus at that! Better than OSX) and the repeated indicators on both screens is really useful. Much rather get Unity working well than jumping ship.

---

### Post by geoffm on 2011-05-01
bump, I was just having the same thoughts

---

### Post by waffleguy4 on 2011-05-01
I'm having the same problems/frustrations. 

Additionally, I'm not sure if this was part of what you were describing, but the Ubuntu circle button (read: windows start button) is at the top left of my right monitor and the side bar is on the left side of the left monitor. Thus, I am unable to use the sidebar with my mouse because the hover area is on my right monitor and the sidebar on my left monitor. It works if I use my super key (read: windows key).

All this on top of lots of Nvidia problems I was having early. Very frustrating.

---

### Post by altintx on 2011-05-01
> **waffleguy4 said:**
> the Ubuntu circle button (read: windows start button) is at the top left of my right monitor and the side bar is on the left side of the left monitor. Thus, I am unable to use the sidebar with my mouse because the hover area is on my right monitor and the sidebar on my left monitor.

I haven't seen that, no. The Ubuntu button is on top of the dock. But, in experimenting, I did see if I'm running classic, with manual panels, and the Global Menu applet added to the panel, but Unity Compiz module is NOT active, I can get something similar to that. Hard to say it is the same thing because it feels so glitchy. But any chance that's what you've got?

---

### Post by Tekmoor on 2011-05-01
I'm also having some serious issues with dual monitors, such as in some cases I can't move windows from my secondary monitor onto my primary and I also can't have windows on my primary monitor maximized or else the window disappears.

@altintx did you find out how to make your primary monitor change permanent? I tried adding the xrandr as a startup command but that didn't do anything...

---

### Post by altintx on 2011-05-01
> **Tekmoor said:**
> @altintx did you find out how to make your primary monitor change permanent? I tried adding the xrandr as a startup command but that didn't do anything...
So far I've only logged out and back in, not restarted, but it's stuck without doing anything. Seems like video has got to be re-initializing because the login screen is mirrored while actual desktop is spanned.

---

### Post by altintx on 2011-05-02
> **Tekmoor said:**
> @altintx did you find out how to make your primary monitor change permanent? I tried adding the xrandr as a startup command but that didn't do anything...

Stand corrected. Stuck through logout but not through reboot. Made a startup item that seems to work, though (three back-to-back reboots and it's coming up consistently)

Command: ```
/usr/bin/xrandr --output VGA1 --primary
```Your intended primary screen may not be VGA1, of course.

---

### Post by Tekmoor on 2011-05-02
Great that command is working! Thanks

I did not specify the full path to xrandr which didn't work for some reason.

---

### Post by saschi on 2011-05-04
Until today the xrandr command worked very well for me. Since today , all it does is put the start menu button on my other screen, while the sidebar stays where it is. This is very frustrating!!

---

### Post by waffleguy4 on 2011-05-06
saschi, this is what I am experiencing also. should I not be using 11.04 yet? I just happened to jump back into Linux a few days after it was released out of beta.

---

