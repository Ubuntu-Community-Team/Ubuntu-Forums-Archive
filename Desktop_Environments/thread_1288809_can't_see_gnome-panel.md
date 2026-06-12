---
title: "can't see gnome-panel"
date: 2009-10-11
forum: Desktop Environments
---

### Post by kolas on 2009-10-11
Hi, I can' see my gnome-panel!! it's really annoying. I had gnome set up with two monitors, and now i'm only using one. could that have something to do with it? I've run gnome-display-preferences and my monitor is set up correctly.

I tried removing my ~/.gnome2 and ~/.gnome-private directories but it made no difference.

I really just want to reset gnome's preferences. How do I do that???

---

### Post by coldReactive on 2009-10-11
sudo apt-get purge gnome-panel (this might remove a lot of gnome stuff.)

Then, reinstall it: sudo apt-get install gnome-panel.

PURGE command of apt-get removes all the settings/etc. See if that works.

---

### Post by GenericGuy on 2009-10-11
It seems gnome is placing the panels on the secondary display, try disabling it on System > Preferences > Display

---

### Post by kolas on 2009-10-12
> **GenericGuy said:**
> It seems gnome is placing the panels on the secondary display, try disabling it on System > Preferences > Display

As I said, I can't see the panel, so I can't get to the System menu. I have made sure only one display is enabled in gnome-display-preferences.

---

### Post by kolas on 2009-10-12
> **coldReactive said:**
> sudo apt-get purge gnome-panel (this might remove a lot of gnome stuff.)

Then, reinstall it: sudo apt-get install gnome-panel.

PURGE command of apt-get removes all the settings/etc. See if that works.

Thanks! I'll try that and post here with the results.

---

### Post by coldReactive on 2009-10-12
> **kolas said:**
> As I said, I can't see the panel, so I can't get to the System menu. I have made sure only one display is enabled in gnome-display-preferences.

What's your graphics card? NVidia, ATI or Intel?

---

### Post by zeroseven0183 on 2009-10-12
Why was it 'preferences'?

---

### Post by coldReactive on 2009-10-12
> **zeroseven0183 said:**
> Why was it 'preferences'?

Yeah, was wondering that too, isn't it properties?

---

### Post by zeroseven0183 on 2009-10-12
I think it should be **gnome-display-properties**

---

### Post by kolas on 2009-10-12
> **zeroseven0183 said:**
> I think it should be **gnome-display-properties**
yeah, that's what i meant

---

### Post by kolas on 2009-10-12
> **coldReactive said:**
> What's your graphics card? NVidia, ATI or Intel?
i have an ATI Radeon X850

---

### Post by kolas on 2009-10-12
> **coldReactive said:**
> sudo apt-get purge gnome-panel (this might remove a lot of gnome stuff.)

Then, reinstall it: sudo apt-get install gnome-panel.

PURGE command of apt-get removes all the settings/etc. See if that works.


I purged it, reinstalled it, then did `/etc/init.d/gdm restart` but it didn't work!

---

### Post by zeroseven0183 on 2009-10-12
I assume you still have the other monitor with you, right? If yes, how about you try to reset it with the other one connected?

---

### Post by kolas on 2009-10-12
> **zeroseven0183 said:**
> I assume you still have the other monitor with you, right? If yes, how about you try to reset it with the other one connected?

Unfortunately, the other monitor is no longer in my possession. Perhaps I should just purge gnome and reinstall. What is the meta-package name for all of gnome? gnome-base?

---

### Post by zhocchao on 2009-10-12
Perhaps it could help to have a look at:

~/.config/monitors.xml

---

