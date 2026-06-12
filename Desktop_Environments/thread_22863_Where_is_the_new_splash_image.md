---
title: "Where is the new splash image?"
date: 2005-03-30
forum: Desktop Environments
---

### Post by nanaban on 2005-03-30
I noticed that the splash image of gnome was changed to a rectangle, slick image after I update my desktop. I like it a lot, but I don't see it on my laptop after updates. Any idea why?

---

### Post by soul_rebel on 2005-03-31
andrea@soul-rebel:~ $ cd /usr/share/pixmaps/splash/
andrea@soul-rebel:/usr/share/pixmaps/splash $ ls
gnome-splash.png         ubuntu-people-450x300.png  ubuntu-splash.png
ubuntu-logo-508x340.png  ubuntu-polished-metal.png
andrea@soul-rebel:/usr/share/pixmaps/splash $ ls -l
totale 240
-rw-r--r--  1 root root  37752 2005-03-29 13:39 gnome-splash.png
-rw-r--r--  1 root root  46290 2005-03-28 02:08 ubuntu-logo-508x340.png
-rw-r--r--  1 root root 139606 2005-03-28 02:08 ubuntu-people-450x300.png
-rw-r--r--  1 root root  11373 2005-03-28 02:08 ubuntu-polished-metal.png
lrwxrwxrwx  1 root root     25 2005-03-29 08:26 ubuntu-splash.png -> ubuntu-polished-metal.png

Look at the ubuntu-splash symlink

---

