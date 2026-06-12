---
title: "Getting back to the default theme"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Rezn on 2007-01-29
Hello all,

I've been messing around with the themes and layouts in Gnome and have made a complete mess of it.

I was wondering if there is a way of getting back to the default settings you get when you log in for the first time.

---

### Post by taurus on 2007-01-29
Try System -> Preferences -> Theme.  And from the list, pick the default one again.

---

### Post by Rezn on 2007-01-29
That's not going to work as I deleted the top bar and moved all the icons around.

I was following this guide here: [http://www.mbhoy.com/19-01-2007/howto-simply-stunning-linux-desktop](http://www.mbhoy.com/19-01-2007/howto-simply-stunning-linux-desktop) but after I finished I realised I made it sort of like windows and that's not what I want.

Thank you for your help.

---

### Post by bonzodog on 2007-01-29
There is a way of doing this - go into your home dir, and delete the gconfd directories, and the gtkrc2.0 file.

BUT - be warned, the gconfd dirs will store settings for a lot more than just the desktop theme - they also store things like game scores, any settings for beryl/metacity, and custom settings for other gnome apps. Deleting them will restore default settings for all gnome apps on your system!

---

### Post by david.rahrer on 2007-02-04
Would backing up these directories/files before messing around with the look and feel, then restoring afterward if you went too far be a good way to do it?  I was about to mess around myself.  Also, would that include .gconf?  Gconfd looks pretty empty.

---

