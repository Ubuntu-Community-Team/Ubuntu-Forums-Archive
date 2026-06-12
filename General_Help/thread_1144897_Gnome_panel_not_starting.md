---
title: "Gnome panel not starting"
date: 2009-05-01
forum: General Help
---

### Post by MorayJ on 2009-05-01
Hi,

It's turned out that when I log on, gnome-panel is not starting.  I just have my wallpaper. I can use a shortcut key to open a terminal and run gnome-panel and it all seems normal.

Just occurred to me that I don't know where you look quickly to tell you what version of Ubuntu you're running! It's not jaunty as I haven't done the latest update, so I guess it's intrepid

I don't believe I've change anything, other than accepting updates as suggested by the automatic updater.

Why might this be? And does anyone know where I should be looking to fix this?

Thanks

MorayJ

---

### Post by gettinoriginal on 2009-05-01
System > Admin > System Monitor > System Tab, will tell you your distro.
About the panel, are you sure it is not just on autohide or pulled to the side by the hide buttons ??  Open panel with terminal, right click on it, properties, and be sure that autohide and hide buttons are unticked
[ATTACH]111982[/ATTACH]

---

### Post by MorayJ on 2009-05-01
Thanks for checking this out. Yes, it's Intrepid.

Panel isn't set to autohide though.

Still looking...

MorayJ

---

### Post by MorayJ on 2009-05-02
OK, looks like my search may not have been as thorough as it could have been as I was in the middle of a project and researching why essential parts of my desktop had disappeared was not something I had much time to play with.

Looks to me like this is something that has been updated somewhere for the general upgrade to jaunty. Although I've not upgraded it has affected me, presumably in a package update.

The solutions that I've found in these forums seems to be add the following two commands to your startup applications. (System->Preferences->Sessions)

gnome-panel #That brings back the menu at the top/bottom
nautilus -n #That brings back desktop icons.

Any comments are welcome which may shed light on the problem or offer alternate solutions.

Cheers
MorayJ

---

### Post by MorayJ on 2009-05-03
...and for anyone still listening, still in the middle of my project, and suspecting a lot of other minor problems. Seem to be getting usb drives being write only to root. No time to research though.

Cheers
Moray

---

### Post by MorayJ on 2009-05-06
...and holding down my backspace key doesn't continue deleting text and holding down the cursor only moves one character. Weird, but couldn't swear that hadn't started before.

Changed 'Update settings' so that it doesn't install recommended updates and only installs security ones. Probably best for a production machine I'm now thinking.

---

### Post by MorayJ on 2009-05-06
Fixed in System-Prefs-Keyboard "Key presses repeat..."

I didn't change any of this so it's either an update or I've been invaded.

---

### Post by MorayJ on 2009-05-07
Last one on this thread - bit the bullet and upgraded to jaunty. Was wary as nvidia caused huge probs in the last upgrade. Immediate impression is that things are sorted. Earlier, the icons on my gnome menus had vanished as well and that's something I hadn't fixed manually. They are now back. Great look too!

Anyway, TTFN
MorayJ

---

