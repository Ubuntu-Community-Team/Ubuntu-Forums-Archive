---
title: "[SOLVED] Slow Keyboard Rate in Kubuntu 8.10"
date: 2008-11-05
forum: Desktop Environments
---

### Post by fornix on 2008-11-05
I installed Kubuntu 8.10 and it was working fine for some days.
Suddenly I started getting a weird problem.
Once I log into kde, I have to hold down any key for around 2 seconds for the key to get registered and then it repeats very fast.
I don't think it is a problem with X server as this problem doesn't occur for gnome and xfce. I've installed all the 3.
Even while logging in, in gdm, I can type normally.
Is this some kind of a bug with kde4.1?

Any help appreciated.

---

### Post by fornix on 2008-11-06
Just to add, I am using a USB Keyboard.

---

### Post by jackashe on 2008-11-14
I have the same problem.  Everything has been fine for about a week, and I was playing a game (running under wine) and suddenly things were not right.  Like you said to get (e.g) a letter to be pressed, i have to hold the key for a second, at which point the repeat rate kicks in, so its almost impossible to type commands or correct typos.  did you find a resolution?  I think I hit some combination of meta and other keys to mess things up.  I searched around some and found some people talking about something similar, but they were changing xorg.conf and reinstalling KDE to no avail.  I really hope I don't have to resort to that.

---

### Post by jackashe on 2008-11-14
I think I found it after pouring through all of the system settings.  No idea how I activated it by hitting a random combo of buttons while playing a game, but here's what fixed it for me:

"System Settings" -> "Accessibility" -> "Keyboard Filters" tab.  the "use slow keys" was checked, with the default being 500 msec delay.  An utterly useless feature unless the repeat rate is also altered, since as soon as the system acknowledges that you have pushed the key it is practically  already repeated two times.  Hope this helped!

---

### Post by jackashe on 2008-11-14
I found how I activated it.  in the same "Accessibility" menu, the final tab is called "Activation Gestures" and the first check box is "Use gestures for activating sticky keys and slow keys".  Well if you right-click, it tells you that the "gesture" for slow keys is "hold down shift for 8 seconds".  IMHO this is a terrible "gesture" and is pure mimicry of MS Win.  

<rant> windows stick keys accessibility is utter garbage, especially because when it first pops up you had better say OK to turning the feature on, then turn it off in the control panel.  if ypu say cancel, your meta keys are broken until you reboot. </rant>

<morerant>
I don't know if prior versions of KDE have a "gesture" like this to turn on a feature that initially makes it seem like your keyboard just broke.  However, there is a certain hand gesture that comes to mind right now given the frustration this caused me, and possibly others.  This will have to be the very first thing I turn off on each version of KDE I use to avoid getting bitten by it ever again.  Holding a key for a few moments should *not* ever be considered a gesture to change a configuration as drastic as this, at least not by default!
</morerant>

---

### Post by jetpeach on 2008-11-15
i agree that gesture is crummy - we should suggest to kde4 in a bug that they should change the gesture...

---

### Post by jetpeach on 2008-11-15
[http://bugs.kde.org/show_bug.cgi?id=119607](http://bugs.kde.org/show_bug.cgi?id=119607)

the above bug is for improving the dialogue that comes up - but here's what i found, at least in Kubuntu 8.10. in the activation gestures preferences area, the "show a confirmation dialog whenever a keyboard accessibility feature is turned on or off" was NOT enabled by default (is it for you? what is it on the default 8.10 install?). this should _definitely_ be enabled by default, so people know when accessbilities are turned on... i stated this in the bug.

---

### Post by fornix on 2008-11-16
> **jackashe said:**
> I think I found it after pouring through all of the system settings.  No idea how I activated it by hitting a random combo of buttons while playing a game, but here's what fixed it for me:

"System Settings" -> "Accessibility" -> "Keyboard Filters" tab.  the "use slow keys" was checked, with the default being 500 msec delay.  An utterly useless feature unless the repeat rate is also altered, since as soon as the system acknowledges that you have pushed the key it is practically  already repeated two times.  Hope this helped!

Ah! Mine was enabled too. God knows how it got enabled. The kubuntu accessibility feature disables the able user as well! :)

---

### Post by carcolo on 2009-04-08
I find this rather a shocking feature; turning you pc essentially useless with no clue as to what happened. 

This sort of thing should only be turned on if you actually enable it in some sort of menu option, preferably with a permanent warning on screen when enabled.

---

