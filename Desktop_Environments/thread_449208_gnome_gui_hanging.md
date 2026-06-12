---
title: "gnome gui hanging"
date: 2007-05-20
forum: Desktop Environments
---

### Post by What_How_Now on 2007-05-20
Couldn't find any previous threads relating to this, as it's weird. To be honest, I don't even know where it came from, I haven't upgraded anything in the past few days.

Various elements of my GNOME desktop and windows seem to hang at random for anywhere between ten seconds and three minutes...it's really frustrating when I want to open a new program or click on my favorites bar in Firefox. Any ideas as to what could be causing this? My system's mid-range: plenty of power for my usual activities; nothing is eating up processor time or memory or network bandwidth. My graphics card is a little old, it's a Geforce 440 Go that's supported under nvidia's newer legacy driver. I already checked the Xorg log: nothing's going on there, no warnings, no errors.

Edit:
Strangely, right clicking started working in an odd way. Now GNOME is bringing up the right click context menu over the last panel or window that I clicked when everything else freezes up. This still isn't optimal behavior. Are there any settings I should look into?

---

### Post by solomarv on 2007-05-20
I experienced the same problem earlier, but it went away after i disabled esd. Try killing esd. The simplest way is to run "killall -9 esd". Gstreamer should be smart enough to switch to ALSA output at that point.

---

### Post by What_How_Now on 2007-05-20
Killing esd didn't change anything.

Interestingly, alt-tab does not work when this oddity occurs. The tty consoles catch all of my keystrokes, so it seems that some gnome, metacity, or X issue is at fault.

edit: resolved, I just wiped all the gnome settings. still a strangle issue though.

edit 1: issue is back even after wiping gnome's settings... this is quite annoying.

---

### Post by What_How_Now on 2007-05-20
Bumping this, since this is a somewhat critical issue to me.

The problem seems to affect GTK applications, including the GDM login screen itself. Once an area of a window such as a list or a series text box has been selected, the window manager does not respond to clicks on other windows or other parts of the same window, such as buttons.

Any insights or logs that I could provide to assist this diagnosis? I honestly have no idea why this is happening, I haven't updated or installed anything besides (I think) a metacity update in the past week.

---

