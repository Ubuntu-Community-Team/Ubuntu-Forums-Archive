---
title: "Firestarter tray icon"
date: 2005-12-25
forum: General Help
---

### Post by Ocxic on 2005-12-25
I have a new black theme and the firestarter icon in the tray has a white box around it, it there a way to change that icon so the backrounf is black instead of white?

---

### Post by ils_systems on 2006-01-01
If you download the firestarter source from their website and look at the images that come with the package, they are transparent.  It's something else in the code that puts the gray box around the icon.  As a workaround, I edited all the images in the source package, and changed them from transparent to having a  dark background and then reinstalled firestarter by running make and make install.  This put a dark background behind the firestarter icon, but if you change your theme back to a light color one, the background around the icon will stay dark.  A more permanent fix would involve changing the actual code that affects the background.  I'm attaching the firestarter executable which has the dark background.  To use it, just place it in /usr/sbin in place of the original file.

---

