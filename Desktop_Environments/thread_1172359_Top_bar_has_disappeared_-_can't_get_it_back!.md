---
title: "Top bar has disappeared - can't get it back!"
date: 2009-05-28
forum: Desktop Environments
---

### Post by jim.hatley.tech on 2009-05-28
Hi all,

I don't know why, but the bar at the top of my desktop has disappeared, and I don't know how to restore it. I have seen advice to enter commands in terminal, but without the bar I don't know how to access terminal! Sorry if this is a dumb question guys, but please help me out - my netbook is effectively bricked right now!

---

### Post by mrog on 2009-05-28
CTRL-ALT-F1 will get you to a terminal.

You could also try this:

ALT-F2. Enter "gnome-panel" in the dialog.

---

### Post by UbuntuNerd on 2009-05-28
if you still got one panel right click on it and click new panel that will give you a new top panel then just right click on the new panel and hit "add to panel" to add all the things back. 
I suggest adding the main menu so you can launch the terminal then type this command to restore everything to default like it was before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by heidipj on 2009-06-03
The problem may be with the 'desktop-switcher' bug - here [https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)

---

### Post by zero1one0 on 2009-06-03
here is a solution
this will cause you to only have your top and bottom panels to the default settings
UbuntuNerd is correct but my answer goes into more detail
and it shows how to acces the terminal without a panel

this was posted at:  [http://ithink88.blogspot.com/2009/05/restore-panel-and-menu-bar-in-ubuntu.html](http://ithink88.blogspot.com/2009/05/restore-panel-and-menu-bar-in-ubuntu.html) 
this was posted by:  i@think

**Sunday, May 17, 2009**

   ** [Restore Panel and Menu Bar in Ubuntu]("http://ithink88.blogspot.com/2009/05/restore-panel-and-menu-bar-in-ubuntu.html") **
   Accidentally deleted the top gnome panel in my ubuntu box, and I can't get anything, neither the terminal to pop out. So, how to get the panel back without too much hassle?

So, let's turn to google and see. A quick google (see[ here]("http://lists.ethernal.org/oldarchives/cantlug-0610/msg00563.html")), and typing this:

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

(A screenshot below showed the same thing)


[[IMG]http://3.bp.blogspot.com/_svaSXZW1cOE/Sg_kex-etsI/AAAAAAAAAW0/l3Y68Ag4Td0/s400/gnome-desktop.bmp[/IMG]]("http://3.bp.blogspot.com/_svaSXZW1cOE/Sg_kex-etsI/AAAAAAAAAW0/l3Y68Ag4Td0/s1600-h/gnome-desktop.bmp")


will get your panel back! But, wait a minute, there is no terminal and how do I get terminal up?

Press Alt and F2 at the same time and select terminal.

Btw, I can't get that Ctrl + Shift + T to work.

- wong chee tat :)

---

### Post by Rany . on 2009-06-03
Both my top and bottom panels are gone after removing evolution, the e-mail client sucked, keep getting grey screen & have long waits for each e-mail to be formatted, its sluggish.
Good thing I got Gnome-Do to call up the terminal and gnome-panel, coz Alt-F is not working too...

---

### Post by Rany . on 2009-06-03
I added gnome-panel to Startup applications. Now the panels are loaded.

---

### Post by jim.hatley.tech on 2009-06-05
Thanks for the assistance guys. Trawled the forums and managed to get the panels back - it's part of a known bug in the desktop switcher, but looks like being fixed imminently, if not already. Happy to stick with proper desktop anyway, so no problem. Thanks again everyone!

---

### Post by mul01 on 2010-09-11
thanks guys i had same problem with my 10.04 LTS and now it has returned thankyou:D

---

