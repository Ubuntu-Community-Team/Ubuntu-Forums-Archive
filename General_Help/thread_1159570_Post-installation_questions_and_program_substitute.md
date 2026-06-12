---
title: "Post-installation questions and program substitutes"
date: 2009-05-14
forum: General Help
---

### Post by Lockheed on 2009-05-14
I have just installed ubuntu but to use it as my main system I need substitutes for the following Windows programs:

- **Subedit** - highly-customizable movie player which can work in a very minimalistic mode where only the movie is shown. No menus, no buttons, nothing. Scroll should change volume and it should have an option to define arrows to scroll the movie 5s and 60s.
- **Total Commander** - gnome commander quits whenever I try to search for a file. Besides, it is a very poor choice in comparison to TC.
- **objectDock** - I need to get rid of the top and bottom bars
- **_rmclock_** (undervolting)


Also, questions:
1. Why is my disk much louder in Ubuntu than in Windows? I can hardly hear it under windows, but Ubuntu hurts my ears.
2. Change the top/bottom image of the compiz cube (something like aquarium would be nice) and the background behind the cube
7. Replace speaker beep on error with some kind of sound-card originating sound

---

### Post by Lockheed on 2009-05-16
Bump

---

### Post by kpkeerthi on 2009-05-16
mplayer for minimalistic video player. Right-click on your video file -> properties -> open with -> enter **/usr/bin/mplayer** under command. Double-click to open. See **man mplayer** for keyboard shortcuts.

Brasero for iso -> dvd. Ubuntu (jaunty) comes with it preinstalled.

To display partition, you should use **sudo fdisk -l**

Turn off beep: See [http://ubuntuforums.org/showthread.php?p=7161976]("http://ubuntuforums.org/showthread.php?p=7161976")

---

### Post by Lockheed on 2009-05-16
I find mplayer very limited in terms of assigning keys to its functions. E.g. how do I assign arrow left/right to 5sec back/forward?
Also, i cannot see any way to disable the control panel so just the picture is visible.

Many thanks for answers to the other 3 problems.

---

### Post by kpkeerthi on 2009-05-16
The control panel appears when you run **gmplayer**. **mplayer** does not show any control panel.

---

### Post by Lockheed on 2009-05-16
I mean this box in the bootom ritght corner:
[http://svn.rpmforge.net/svn/trunk/web/freshrpms.net/docs/dvd/screenshot-mplayer.png](http://svn.rpmforge.net/svn/trunk/web/freshrpms.net/docs/dvd/screenshot-mplayer.png)

Is is possible to set to so it only appears when you move your mouse?

---

