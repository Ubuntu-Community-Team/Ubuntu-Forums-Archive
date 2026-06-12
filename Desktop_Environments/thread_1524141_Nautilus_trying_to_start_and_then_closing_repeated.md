---
title: "Nautilus trying to start and then closing repeatedly"
date: 2010-07-04
forum: Desktop Environments
---

### Post by mwhite212 on 2010-07-04
I keep getting "Starting File Manager" flashing on and off on the bottom tool bar in Ubuntu 10.04. The icons on my desktop keep blinking on and off and I can't access any folders! Help! It happened after saving an SVG file to my desktop in Inkscape. Not sure that's anything to do with it. I rebooted twice and it is continuing to do the same thing.

---

### Post by lkjoel on 2010-07-04
> **mwhite212 said:**
> I keep getting "Starting File Manager" flashing on and off on the bottom tool bar in Ubuntu 10.04. The icons on my desktop keep blinking on and off and I can't access any folders! Help! It happened after saving an SVG file to my desktop in Inkscape. Not sure that's anything to do with it. I rebooted twice and it is continuing to do the same thing.
Ok, this is probably not the problem, but do you have a good anti-virus software installed?
If so, use it.

---

### Post by ThomasB2k on 2010-07-04
This happened to me too, and unfortunately I was stuck with having to reinstall. :(

---

### Post by zfreak7c5 on 2010-07-05
You may want to try logging in with a different/new user to see if it could be something in your profile.  If it works fine there you'll know it is the profile or a setting.  If it doesn't work you may try reinstalling nautilus.

---

### Post by lkjoel on 2010-07-05
There should be something like:
~/.gconf
or
~/.config
or
~/.conf
Go in one of them, then check for nautilus.
Delete that folder.

---

