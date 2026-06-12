---
title: "Gnome desktop does not remember window position/size - still?"
date: 2010-07-07
forum: Desktop Environments
---

### Post by taylorkh on 2010-07-07
My searching shows a lot of complaints on this issue over the past few years - and no solutions.  Just wondering if this still the case - my experience tells me the issue is still present - are there any solutions? I am running Ubuntu 10.04 LTS.

The issue is that Gnome will not "remember" the size and location of the window in which an app was last run.  For example - I run Disk Usage Analyzer and stretch the window to be the full height of the screen and about half the width of the screen and move it to the far left of the desktop. I then close the app. The next time I run it the app comes up in a "default" window size, not the size I last used, positioned randomly on the desktop.

TIA,

Ken

p.s. I should add that some apps seem to remember their prior window size/position. For example OpenOffice.org, Firefox, Nautilus.

---

### Post by jounihat on 2010-08-02
This bug is just ridiculous. It's the #1 productivity killer, and no one wants to fix it because "it's not their business". Resizing and moving 20 windows every time Gnome dies or dual-booting or restarting the computer is so annoying, but what can we do?

In my opinion the window manager should always remember all window positions and sizes UNLESS the program itself wants to override this.

---

### Post by taylorkh on 2010-08-03
Amen to that!

---

### Post by kpothi on 2010-11-14
> **jounihat said:**
> This bug is just ridiculous. It's the #1 productivity killer, and no one wants to fix it because "it's not their business". Resizing and moving 20 windows every time Gnome dies or dual-booting or restarting the computer is so annoying, but what can we do?

In my opinion the window manager should always remember all window positions and sizes UNLESS the program itself wants to override this.

Yep! I wish I knew how to fix this! It's damn so important (at least for me!)

---

### Post by CowzRule on 2010-11-14
If your hardware is able to run Compiz, there are setting in CompizConfig Settings Manager to place windows where and how you want them. The plug-ins "Place Windows" and "Windows Rules", under the heading "Window Management", is where those options would be set.

Hope that helps.

---

### Post by kpothi on 2010-11-14
> **CowzRule said:**
> If your hardware is able to run Compiz, there are setting in CompizConfig Settings Manager to place windows where and how you want them. The plug-ins "Place Windows" and "Windows Rules", under the heading "Window Management", is where those options would be set.

Hope that helps.

Thanks for your tip. I would try this soon.

---

### Post by kpothi on 2010-11-18
> **CowzRule said:**
> If your hardware is able to run Compiz, there are setting in CompizConfig Settings Manager to place windows where and how you want them. The plug-ins "Place Windows" and "Windows Rules", under the heading "Window Management", is where those options would be set.

Hope that helps.

Hi CowzRule,

I just tried it. I was amazed with the options available. Currently I use 'smart' option under 'Place Windows' plugin that solved most of my problems..

I also got to know a few other plugins that I always looked for in a linux box. Particularly, 'Put' and 'Grid' plugins, these two offer much more options than 'WinSplit Revolution' available for XP.

Thanks so much for guiding me.

Pothi

---

### Post by asmoore82 on 2010-11-18
You're barking up the wrong tree, there is no Gnome bug here.

It's not the duty of the Window Manager to remember window sizes;
that's up to individual apps. You should file a bug with those apps.

However, Compiz "Desktop Effects" does have some options for initial window placement.

---

### Post by owlcroft on 2010-12-13
It is not the wrong tree.  Well, strictly maybe: it is not gnome as such, but rather the window manager, metacity (or compiz or whatever).

The matter has languished, despite extensive, major, continuing user complaints over the years because of the hard-headed "not ***my*** problem" attitude as between the window-manager developers and the app developers.  A long, interesting, and indicative metacity Bug Report ([https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/124315](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/124315)) tells the story pretty well.

The gist is that the methodology is well known and not difficult to implement: it requires modest work by the window-manager team to implement a management system based on an existing parameter, coupled with app developers making their apps properly supply that parm to the window manager.  Till the manager developers get off the schnie and install their part of the deal, the app developers are free to say "What am *I* supposed to do?" because there really isn't much.  (The idea that each app should manage its own windows is tempting, and some do, but it is a needless major duplication of effort that ought to be centralized in the WM.)

---

### Post by olderUser on 2011-05-10
I use open office Calc to produce wide documents and narrow documents. I find it a pest to have to constantly adjust the window size and location.

Isn't it possible for each document to save its own size and position so that when a document is opened it appears just as it did last time you used it?

---

