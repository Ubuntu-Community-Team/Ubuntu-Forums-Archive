---
title: "Gtk2 + Firefox + Gnome + Metacity = too slow"
date: 2006-07-22
forum: Desktop Environments
---

### Post by krausest on 2006-07-22
Do you have any tips and tricks to make gnome, gtk2 applications or the UI of firefox faster?
My laptop has a Geforce 6800 with lastest binary drivers installed and runs OpenGL perfectly, but switching between gtk2 based apps like eclipse, firefox, nautilus or even gnome-terminal is a pain. It's flashing, you can see parts of the redraw and popup dialogs take some milliseconds too long. All in all it simply feels slow.

Here's what I already tried:
* Running on 686 kernel (or a custom compile 2.6.17-ck1 kernel). Doesn't help with UI speed at all.
* Swiftfox / Fasterfox apparently don't influcene firefox slowness when scrolling in the bookmarks or waiting for the "Close all tabs" dialog to finish drawin...
* xcompmgr helps switching between running windows but make all OpenGL based programs run with half speed (like xcfe with composite enabled)

Some questions:
* Do themes influence Gtk2's rendering speed? Which theme is faster?
* Are there any optimized Gtk2 builds that speed things up?

---

### Post by RawMustard on 2006-07-22
Welcome to the Gnome Desktop!

I switched to XGL/Compiz to get better performance, you should be able to also with that gfx card without problems.

How much ram do you have, the Gnome desktop is a ram pig, the more the better!

---

### Post by krausest on 2006-07-22
Ram shouldn't be the big problem - I've got 1GB.

Last time I tried Xgl OpenGL didn't work as I needed. Applications running inside Xgl had only some kind of Mesa renderer, all OpenGL 2.0 extensions were missing. From what I know this will change only with a future NVidia driver that supports the texture_from_pixmap extension...

---

### Post by psylence on 2006-07-22
This should help with that problem in the mean-time: [http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

---

