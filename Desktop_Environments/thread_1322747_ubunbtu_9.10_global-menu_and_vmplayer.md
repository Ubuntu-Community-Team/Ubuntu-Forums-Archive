---
title: "ubunbtu 9.10 global-menu and vmplayer"
date: 2009-11-11
forum: Desktop Environments
---

### Post by svenole on 2009-11-11
I'm running 9.10 and the other day I decided to try the mac themes on my laptop. Obviously I had to fix some issues since I am running 9.10 and all descriptions on how to do this is based on earlier release, but after some I got it to work. 

However there is one big hit. vmplayer does not work anymore. I'm running vmplayer 3.0 and it fails with a gtk error: GLib-GObject: Attempt to add property GtkMenuBar::local to class after it was derived

Now, I use vmplayer a lot and need to drop this Mac theme trial if I can not get this to work. Seems like the software installed (maybe global-menu) messes up the gtk. Anyone out there who knows if this is fixable?

---

### Post by J-Buntu on 2009-11-11
I'm guessing you've tried this ? Right click on the Global Menu Applet, select preferences, then in the new window, UNCHECK - Enable Global Menu For GTK applications ?[URL="http://ubuntuforums.org/member.php?u=252366"] 
[/URL]

---

### Post by svenole on 2009-11-11
Thanks for the tip. I had not checked this and vmplayer starts when global-menu for Gtk-apps is disabled. However, the whole point of the Global Menu is more or less gone when running like this so I will probably deinstall the whole thing. 

Thanks.

---

### Post by J-Buntu on 2009-11-11
I know it sucks, there are currently a few things that don't work with Global Menu at all, or lack full functionality. Currently on Karmic the system monitor doesn't work when Global Menu is on and Firefox isn't compatible either (Global Menu doesn't show the Firefox menu) Sorry i can't help you further, hopefully they'll sort out these problems soon.

---

