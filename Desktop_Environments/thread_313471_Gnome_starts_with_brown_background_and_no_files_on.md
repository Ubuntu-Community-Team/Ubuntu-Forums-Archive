---
title: "Gnome starts with brown background and no files on desktop"
date: 2006-12-06
forum: Desktop Environments
---

### Post by rigol on 2006-12-06
Hi,


Since the morning I'm having this problem: when I log in into gnome, it starts without my background picture and the files on the desktop are not shown. I can access these files pretty fine when opening the File Browser Nautilus.

I think it might be related to yesterday when I removed some jobs from the "Current Session" tab in System --> Preferences --> Sesssions. I'm quite sure, one was something with Nautilus (I know, stupid](*,)), but I can't remember. When I have a look at this "Current Session" now, there is no program named something with Nautilus.

How do I get that back?

---

### Post by mcduck on 2006-12-06
try this:

First, run 'nautilus' in a terminal to get Nautilus running.

Then open the Sessions-window, and under 'Current Session' make sure that Nautilus has Order 40 and it's Style is set to Restart, not Normal.

---

### Post by Endolith on 2007-12-14
> **mcduck said:**
> Then open the Sessions-window, and under 'Current Session' make sure that Nautilus has Order 40 and it's Style is set to Restart, not Normal.

Maybe you could explain what that means?

---

### Post by imtheguru on 2007-12-15
System > Preferences > Sessions

---

### Post by Endolith on 2007-12-15
> **imtheguru said:**
> System > Preferences > Sessions

What about it?

---

### Post by mcduck on 2007-12-15
> **Endolith said:**
> Maybe you could explain what that means?

Current Session is where you define what programs are automatically started when you log in. Order tells the order in which they should be started, and setting the Style to Restart instead of Normal means that if you close nautilus it doesn't actually close but restarts instead. Normal would mean the program, it stays closed (like you would like to happen with most of your programs).

These setting are the settings that Gnome has for Nautilus by default.

And yes, you'll find the Sessions window in System/Preferences/Sessions.

---

