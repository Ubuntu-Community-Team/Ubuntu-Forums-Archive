---
title: "Scripting a permanent CTRL / CAPS swap in Gnome?"
date: 2011-03-03
forum: Desktop Environments
---

### Post by duncan_bayne on 2011-03-03
Hi All,

I have a bash script that I use to configure a vanilla Ubuntu (10.10 Maverick) installation to be exactly the way I want it.  I make extensive use of gconftool-2 to configure the desktop, set up shortcut keys, etc.

Now, I'm trying to swap the CTRL and CAPS keys.  I have found two ways of doing this:

[LIST]In Gnome, go to System -> Preferences -> Keyboard -> Layout -> Options and make the change in there.  This works well, but I don't know how to script this; the setting doesn't seem to be stored in the usual place as I can't find it with gconf-editor.[/LIST]

[LIST]Add the line [FONT="Courier New"]setxkbmap -option "ctrl:swapcaps"[/FONT] to my [FONT="Courier New"].bashrc[/FONT] file.  That works too, until I suspend the machine & then resume it.  At that point the CTRL and CAPS behaviour return to normal, until I cause [FONT="Courier New"].bashrc[/FONT] to be run again by opening a new shell.  This behaviour has been reported as a [bug]("https://bugzilla.redhat.com/show_bug.cgi?id=639145") in RedHat.[/LIST]

[LIST]*Edited to add:* JeffG on superuser.com [suggested]("http://superuser.com/questions/252941/scripting-a-permanent-ctrl-caps-swap-in-gnome/252953#252953") adding the call to setxkbmap to my gdm.conf file in the script section; that resulted in a failure to load X on startup.[/LIST]

Could someone please suggest a way of switching those keys that is both permanent, and can be scripted?  I'm sure I must be missing something obvious here ...

---

### Post by deconstrained on 2011-03-04
You may need to change the console keymap, especially if you want the change to be system-wide.

I just recently found this:
[http://www.shallowsky.com/linux/keymap.html](http://www.shallowsky.com/linux/keymap.html)

Of course, make a backup copy of your current keymap before attempting.

---

### Post by gmargo on 2011-03-04
If you're running Gnome, then all you need to do is create a file **$HOME/.Xkbmap** with this content:
```

-option ctrl:swapcaps

```Log out then back in.
Update: I just confirmed that the setting lasts across a suspend/resume.

---

### Post by duncan_bayne on 2011-03-06
> **gmargo said:**
> If you're running Gnome, then all you need to do is create a file **$HOME/.Xkbmap** with this content:
```

-option ctrl:swapcaps

```Log out then back in.
Update: I just confirmed that the setting lasts across a suspend/resume.
Thanks - that works perfectly, & does indeed survive a suspend / resume.  Exactly what I was hoping for :D

---

