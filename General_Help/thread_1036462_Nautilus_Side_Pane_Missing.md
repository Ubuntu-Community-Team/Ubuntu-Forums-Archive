---
title: "Nautilus Side Pane Missing"
date: 2009-01-10
forum: General Help
---

### Post by domoso on 2009-01-10
Hey all. I made the decision to switch my main system to Ubuntu 8.10 from Windows. I was configuring the system, specifically, Nautilus to be more like File Manager and utilizing the side pane. It was visible but, I wanted it to view the directory structure. And I wanted Nautilus to open new directories in the existing Window. So, after I made the appropriate changes I exited the preferences to find the side pane gone.

I did some research on Google and on the forums here. But, it seems everyone that has complained about it missing ended up moving the side pane all the way to the left of the window. The solutions are typically moving the cursor to the left edge of the Nautilus window and acquiring the double arrow cursor to move it back in place. I can assure you that this is not the case here.

I've also tried pressing F9, as documented. This does nothing. When going to the View menu in Nautilus there isn't an option available for "side pane", as documented.

I ran gconf-editor and reviewed the Nautilus settings. It is indicating that the side pane is enabled and has a width of 277. But, there isn't a side pane. I only have a single pane window showing the individual files and directories.

Any help is appreciated. TIA

PS - I've uninstalled and reinstalled Nautilus. I've run dpkg --purge. And reinstalled. No joy. It appears to be retaining my settings from a previous installation. However, I have not found documentation indicating where such settings are stored. Is there a conf file for Nautilus?

---

### Post by domoso on 2009-01-10
Yeah, I never ask the easy Linux questions. You know, the one's where someone else has experienced the problem *sigh*

---

### Post by mc4man on 2009-01-10
I'll let you know if I find anything, just noticed mine is 'gone missing' also (with it enabled, ect.

Find mine by grabbing it carefully and moving to the right.

---

### Post by chex_m8 on 2009-01-10
Yeah it sound like the side pain may have been coverd up by the main window, try dragging the very left screen over to uncover the side pain. Also try right clicking the folder and selecting Browse Folder.

---

### Post by -kg- on 2009-01-11
> **chex_m8 said:**
> Yeah it sound like the side pain may have been coverd up by the main window, try dragging the very left screen over to uncover the side pain. Also try right clicking the folder and selecting Browse Folder.

Of course, domoso already said:

> I did some research on Google and on the forums here. But, it seems everyone that has complained about it missing ended up moving the side pane all the way to the left of the window. The solutions are typically moving the cursor to the left edge of the Nautilus window and acquiring the double arrow cursor to move it back in place. I can assure you that this is not the case here.

I've also tried pressing F9, as documented. This does nothing. When going to the View menu in Nautilus there isn't an option available for "side pane", as documented.

I've looked at the Preferences, and I can't for the life of me find any settings that look like they would even *possibly* create that problem.  What settings did you change? Can you change them back?

Oh, and did you by any chance "move" the pane to another position, like the bottom or the right side?  (Of course, I can't see any way to do *that,* either)

Also, you stated:

> I ran gconf-editor and reviewed the Nautilus settings. It is indicating that the side pane is enabled and has a width of 277. But, there isn't a side pane. I only have a single pane window showing the individual files and directories.

Did you check the size of the Main window in your gconf?  Perhaps that has been set somehow to cover the full screen and not able to be changed.  I noticed that when I resized the panel, that it was the right pane that resized and covered the left pane.  The icons in the right pane scrolled and changed position on resize, while the left pane was just covered up.  So as suggested, the right pane covers the left.

These are the only things I can think of.  The "Side Pane" checkbox under the "View" menu works fine on my computer, as does F9.  I'd personally like to know, since I'm prone to "breaking my computer" while playing with it, from time to time.

:lolflag:

---

### Post by domoso on 2009-01-11
Well, if the main window is covering the side pane I don't know. I'm not getting the double arrows and I've spent like 15 minutes at the left side of the window all up and down it trying to find the double arrow while moving the move very slowly. No double arrow.

What I changed was stuff like open folder in same window, use compact view, a small zoom on default view, show hidden files. It wasn't alot. And I know as well, nothing in there should have caused this problem. All I know is when I went into preferences I had the side pane. When I came out, it disappeared.

I'll check the main window size.

There are not settings for main window size in gconf-editor.

---

### Post by -kg- on 2009-01-12
Ah!  I think I might have found the problem.

Run gconf-editor again and go to the Nautilus Preferences.  Make sure you have the "always_use_browser" check box checked.

I was going through the Preferences trying to figure out what the problem could possibly be, and upon seeing that setting, I unchecked it and launched Nautilus.  Sure as shootin', there was no side pane and I couldn't draw it out.

Hopefully, that should get you back up and going.

---

