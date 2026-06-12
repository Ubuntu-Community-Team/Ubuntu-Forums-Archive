---
title: "Metacity Missing Window Decorations"
date: 2007-12-13
forum: Desktop Environments
---

### Post by linas on 2007-12-13
Hi,

I upgraded to gutsy just a few days ago.  Today, my window manager
does not have any decorations (minimize/maximize/close).  Similar problems have been reported before; my situation seems different; the closest seems to be [http://www.mail-archive.com/debian-bugs-closed%40lists.debian.org/msg147870.html](http://www.mail-archive.com/debian-bugs-closed%40lists.debian.org/msg147870.html)

Some details:
-- After loging in, no window manager ran; I had to start metacity by hand.

-- A prowl through gconf-editor showed that /usr/bin/compiz was the default window manager, even though compiz is not installed. 

-- Running "metacity --replace" now gets the window manager to run when I log in, but still, no window decor.

-- I created a new user account, and logged in. The new user doesn't get window decorations either.  This rules out corrupted ~/.gnome, ~/.gconf entries

-- Curiously, the window menu is shifted over by a few inches, to the right. This is the pull-down menu which has the minimize/maximize/etc. menu entries in it. So perhaps the right-side buttons have shifted too far over?!! (actually, I'm fairly convinced that is the problem!) Or the window title is too wide, and over-writes the decorations???

Some unusual things about my system:
-- Its a new athalon64. (there seem to be some rare ath64-related bugs out there)

-- The current video card is an ancient PCI card, a matrox millenium. Since it has only 4MB ram, and I'm running in 1680x1050 pixels, I have to have 16-bit color turned on (as opposed to normal 24-bit RGB true color).

---

### Post by Drate on 2007-12-14
I had pretty much the same problem a while back; I reinstalled metacity (rebooted to see if it fixed it), nope, ran "metacity --replace" (rebooted to see if it fixed it), yep. Maybe I didn't need the first reboot, but who cares? That process seems to have done the trick permanent.  JUST running replace seemed to only fix it for the session.

[http://ubuntuforums.org/showthread.php?t=626864](http://ubuntuforums.org/showthread.php?t=626864)

^^ my original post

---

### Post by linas on 2007-12-15
Ahh!  I'd previously tried reinstalling metacity, and metacity --replace, with no effect.  Just now, I deleted the apt cache: cd /var/cache/apt/archives; rm meta*  which deletes both metacity and metacity-common. I then reinstalled both (apt-get install --reinstall), did the metacity --replace and bingo! now it works.  Wow! Thanks!

In fact, I'd also seen some other weirdness indicating that some of the downloded files had gotten corrupted, and found that re-downloading and installing fixed those problems. There were only three packages that I know of that were affected. As it happens, I was struggling with a crappy disk drive right around this time (per [http://lkml.org/lkml/2007/6/20/180](http://lkml.org/lkml/2007/6/20/180)) and that probably explains the intermittent corruption.  So all is well. And that effing disk is now gone.

What surprises me is that dpkg did not do any sort of crc or md5 check on the file contents to make sure that corruption hadn't happened ... it just installed corrupted junk. If any dpkg maintainers are reading this, please fix!!

:guitar:

---

