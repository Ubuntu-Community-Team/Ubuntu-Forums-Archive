---
title: "Launcher Arguments"
date: 2011-03-07
forum: Desktop Environments
---

### Post by glittleman on 2011-03-07
Basically I want Banshee to always launch in Desktop 4.  I have Ubutuntu 10.10 Gnome 2.0

Menu Launcher looks like this..


> banshee-1 --redirect-log --play-enqueued %U

Thanks for your help

---

### Post by Krytarik on 2011-03-07
Do you mean "Desktop" or "Workspace" instead? If you mean the latter, read further.

You can use Compiz' "Place Windows" plugin for that, "System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Place Windows".

In the "Fixed Window Placement" tab add a rule to "Windows with fixed viewport", grab Banshee's "class" in the "New" dialog, most probably it's "Banshee".

Greetings.

---

