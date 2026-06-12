---
title: "Bad GUI design"
date: 2008-07-01
forum: Desktop Environments
---

### Post by Dr Eigen on 2008-07-01
What ever happened to that old law of GUI design:  **Always Give The User Feedback**?

I'm not sure who to blame for this, but this principle has been forgotten by whoever put together my desktop (Hardy, Gnome).  For example, if I click the update icon in my Notification Area on my slow machine, nothing happens for quite a number of seconds.  Eventually the updater pops open, but for a while I'm left sitting there wondering if I missed the icon, if my mouse has decided to stop processing clicks, if I should have double-clicked, etc.  No visual feedback of the event at all.

What gives, Ubuntites?

---

### Post by icheyne on 2008-07-01
Maybe your PC is too slow for Ubuntu? How much RAM do you have? Tried Xubuntu?

I don't user the GUI updater. Instead I open a console window and type:

sudo aptitude update
sudo aptitude full-upgrade

---

### Post by ladr0n on 2008-07-01
This isn't really an issue of the computer's speed.  Application launch *should* give visual feedback.  You will at least get the "icon flying at you" thing if you have all of the visual effects turned on, but not everyone wants to waste their system resources on a fancy desktop.

It would be cool to have something along the lines of the bouncing icon under the cursor a la KDE 3.x (but not that specific effect, gnome needs something more elegant :)).  That way the user knows for sure she clicked the correct thing, and her computer is currently processing her request to open such-and-such program.

---

### Post by rainwalker on 2008-07-01
> **ladr0n said:**
> This isn't really an issue of the computer's speed.  Application launch *should* give visual feedback.  You will at least get the "icon flying at you" thing if you have all of the visual effects turned on, but not everyone wants to waste their system resources on a fancy desktop.

It would be cool to have something along the lines of the bouncing icon under the cursor a la KDE 3.x (but not that specific effect, gnome needs something more elegant :)).  That way the user knows for sure she clicked the correct thing, and her computer is currently processing her request to open such-and-such program.

Unfortunately, that effect only happens with launchers in the panel, not stuff in the Notification Area :?

---

### Post by wirah on 2009-04-30
I am inclined to agree with the original author.

I have here a 2.8ghz Core 2 Duo machine with an ATI Radeon HD video card and 2gb of ram. I am running Ubuntu 8.10.

If I click updater there is a 3-5 second delay where nothing happens. I always click it twice by accident. I always forget i've clicked it and click it again.

This is why items in apple's dock bounce. Ours should do something too...

---

