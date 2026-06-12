---
title: "Cairo Dock + Unity + Firefox = confusion"
date: 2011-10-15
forum: Desktop Environments
---

### Post by GarbloJones on 2011-10-15
So i just noticed this minutes ago ...

Whenever i minimize firefox, both cairo dock and unity both freeze until i switch to another workspace. At that point i still can't restore the window (from cairo dock OR unity sidebar) -- i have to hit ALT + TAB to get back to my firefox window

RUNNING:
Ubuntu 11.10 -- 64

side-note: 
I also just realized that when programs are minimized to the upper "system tray" area, i can't open them / right click them. they just ... go there to die i guess...

EDIT: the system tray issue seems to have gone away after a restart...

your help is appreciated.

---

### Post by GarbloJones on 2011-10-15
sorry for the double post but to add to the strangeness of it all ... the minimizing issue doesn't seem to happen when i have gimp open. what the heck??

EDIT: 
OK, upon even further investigation - it seems this problem occurs with any program that is the only one open in that workspace --- if there are two programs open, there are no issues - any one have any ideas? i don't want to ALWAYS think about keeping another program open before minimizing another one.

---

### Post by Copper Bezel on 2011-10-15
Can I ask - what's the purpose of having two docks? I don't have any experience with this particular problem, but it sounds as if Cairo Dock and Unity aren't really usable with one another. 

Also, have you tried using Cairo Dock without the Unity plugin enabled, to see if it does work by itself or whether the problem might be something in Cairo Dock itself?

---

### Post by Gs Dewd on 2011-10-15
I am running the cario dock with unity (Ubuntu 11.10) without any issues.

---

### Post by GarbloJones on 2011-10-16
i actually don't want to be running two docks, but when i disabled unity, i think i really screwed something up - my system tray / task bar disappeared and i was also trying to mess with the global menu. 

anyway --- just came back from fresh install. going to try again.

Gs Dewd, do you know if theres any way to disable the unity launcher while keeping the upper task tray? how do you have yours configured?

---

### Post by Copper Bezel on 2011-10-16
[QUOTE=GarbloJones]i actually don't want to be running two docks, but when i disabled unity, i think i really screwed something up - my system tray / task bar disappeared and i was also trying to mess with the global menu.[/QUOTE]

Okay, you probably didn't actually need to reinstall anything, and the top panel is a part of the Unity plugin. 

To hide the Unity launcher permanently, leaving only the top bar, go into the plugin in compizconfig-settings-manager and set its behavior to Autohide instead of Dodge Window, then disable the Reveal Mode. You could also consider running a different panel in place of Unity's.

That's assuming that the same bug you experienced earlier doesn't resurface, of course.

---

### Post by makitso on 2011-10-17
> To hide the Unity launcher permanently, leaving only the top bar, go  into the plugin in compizconfig-settings-manager and set its behavior to  Autohide instead of Dodge Window, then disable the Reveal Mode. You  could also consider running a different panel in place of Unity's.

I tried running AWN with Unity and configured Unity with the Autohide as described above.  The problem was that any time I launched an app from AWN the unity doc would peek out.  Same goes for any folder on the desktop, if you drag it anywhere.  So,  this forced me install the Gnome 3 shell and run AWN there.  FWIW, I also tried to run Cairo but I prefer AWN.

---

### Post by areeda on 2011-10-17
> **Copper Bezel said:**
> Can I ask - what's the purpose of having two docks? I don't have any experience with this particular problem, but it sounds as if Cairo Dock and Unity aren't really usable with one another. 

Also, have you tried using Cairo Dock without the Unity plugin enabled, to see if it does work by itself or whether the problem might be something in Cairo Dock itself?
I am trying Cairo Dock because it seems the Unity Launch Bar must be in the far left of multiple screens.   I have a dual monitor setup with a 27" 1080p as my main monitor and a 1280x1024 older one to the left.  Both are on switch boxes.  Having the Unity launcher on the small one is ..ugh.. suboptimal (to be nice).

To get this to work I have to lie to nVidia config and say that monitor is on the right so I have to move the mouse off the right edge of the screen to get to the monitor on the left.  Difficult for my feeble brain to get used to.

> **Gs Dewd said:**
> I am running the cario dock with unity (Ubuntu 11.10) without any issues.
Me too. Minimize / restore, launch from either.  I haven't run into this.

> **Copper Bezel said:**
> Okay, you probably didn't actually need to reinstall anything, and the top panel is a part of the Unity plugin. 

To hide the Unity launcher permanently, leaving only the top bar, go into the plugin in compizconfig-settings-manager and set its behavior to Autohide instead of Dodge Window, then disable the Reveal Mode. You could also consider running a different panel in place of Unity's.

That's assuming that the same bug you experienced earlier doesn't resurface, of course.
I have not had any luck with the Compiz Settings.  It seems like if I change anything I loose unity and have to drop down to a login shell and reset unity to get it back.

Joe

---

### Post by Copper Bezel on 2011-10-17
Huh. Yeah, probably best to go with Shell or Fallback, then, honestly, since either will provide a top panel (and Fallback's is customizable and compatible with Compiz.) I didn't realize there were these other problems with the Unity icons popping out, either (because it's been my strategy to just turn off Unity and use, as makitso noted, AWN, which can provide the top panel as well.)

---

### Post by GarbloJones on 2011-10-17
Hey guys, 

just reporting back

1) yea, I tried going to fallback, but its just not the same tasktray (integrated sound stuff, all around bulky-er look) - i'm very OCD when it comes to how my desktop looks.
2) YES - i definitely did NOT need to do a clean re-install :(   --- oh well, ya live and ya learn

3) MOST IMPORTANTLY - if you don't like the global menu, DO NOT unclick "Let file manager handle desktop" (this was in one of the first "Things to tweak" posts when i searched "how to disable global menu")

--- instead, ONLY use this command
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qtnow everything is working beautifully (both literally and figuratively) in harmony.

Thanks for your help all.

---

