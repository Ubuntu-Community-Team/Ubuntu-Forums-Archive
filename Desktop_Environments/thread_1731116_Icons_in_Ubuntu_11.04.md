---
title: "Icons in Ubuntu 11.04"
date: 2011-04-16
forum: Desktop Environments
---

### Post by jrd on 2011-04-16
I have Ubuntu 11.04 (I understand it hasn't been released yet) and my icons are missing on my top panel in Gnome. Did the location for these change since 10.10? I got 11.04 via upgrade. i attached a screen shot of what I'm talking about.

---

### Post by Larkspur on 2011-04-16
> **jrd said:**
> I have Ubuntu 11.04 (I understand it hasn't been released yet) and my icons are missing on my top panel in Gnome. Did the location for these change since 10.10? I got 11.04 via upgrade. i attached a screen shot of what I'm talking about.

They should be there; they're for network manager and sound.  Do the drop-down menus work? Try changing the icon theme in Appearances, to see if the one you're using somehow lost them in the upgrade.

---

### Post by jrd on 2011-04-16
> **Larkspur said:**
> They should be there; they're for network manager and sound.  Do the drop-down menus work? Try changing the icon theme in Appearances, to see if the one you're using somehow lost them in the upgrade.

Let me rephrase my question. The 2 little red circles with the line through them should be drop box and network manager. Instead it's just little circles with lines through them. Why is this?  I'll try changing the theme though and see if it helps. Thanks for the fast reply.

---

### Post by jrd on 2011-04-16
Nope. Still the same thing.

---

### Post by Larkspur on 2011-04-16
> **jrd said:**
> Let me rephrase my question. The 2 little red circles with the line through them should be drop box and network manager. Instead it's just little circles with lines through them. Why is this?  I'll try changing the theme though and see if it helps. Thanks for the fast reply.

Sorry about the mistake: I based it on my own panel.  The reason why they're little circles is that Ubuntu can't find the icons in the place they should be (the network manager icons should be in /usr/share/icons/whatevericonsetyou'reusing/status or in ~/.icons.  I presume Dropbox would put its icons in the same place).  I've read that doing an upgrade instead of an install can cause problems.  Maybe that's what has happened here.

EDIT: Just seen your last post.  Hmm.  Are the icons there?  Check the status folder of your current icon set (in /usr/share/icons) for icons whose names begin with "nm" or "gnome-netstatus."  I don't know which ones the applet uses.

---

### Post by helicase on 2011-04-16
Try removing the notification area from the panel and then adding it again.

---

### Post by jrd on 2011-04-16
Right, that's what I meant when I asked if they changed location. Like did they stop putting icons in /usr/share/icons/hicolor/16x16/apps/? I can't really find anything on it so far.

---

### Post by mc4man on 2011-04-16
Don't use the Classic login in natty too much, maybe doing an upgrade has something to do with.
I gather you could use individual applets in that area or - by default in a fresh install there are just 2
Screen 1 shows - vlc is in the notification area applet, the rest is one applet - 'indicator applet complete' (screen 2
You could try removing all and then setting it up that way or set up as before in maverick from right to left  - indicator applet session, indicator applet, notification area

---

### Post by jrd on 2011-04-16
> **mc4man said:**
> Don't use the Classic login in natty too much, maybe doing an upgrade has something to do with.
I gather you could use individual applets in that area or - by default in a fresh install there are just 2
Screen 1 shows - vlc is in the notification area applet, the rest is one applet - 'indicator applet complete' (screen 2
You could try removing all and then setting it up that way or set up as before in maverick from right to left  - indicator applet session, indicator applet, notification area


That fixed it! Thank you!

---

