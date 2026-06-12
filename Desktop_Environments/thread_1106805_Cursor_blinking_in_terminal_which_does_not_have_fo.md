---
title: "Cursor blinking in terminal which does not have focus"
date: 2009-03-26
forum: Desktop Environments
---

### Post by Arndt on 2009-03-26
When I use several instances of gnome-terminal, it sometimes works this way: the one which has focus (I use focus follows mouse) has a blinking solid cursor, and all the others (if visible) have a non-blinking rectangular outline of the same shape (mostly white).

That's how I want it to work - I'm not irritated by the blinking in the window where I'm working, although I've read that the ability to turn that off was absent for a while, until the gnome people put it back, because many got angry (rightly so, I find).

My problem is that quite often, the cursor blinks also in terminals which do not have focus. I haven't been able to find a pattern to which behave correctly, and which not. Is this a known bug? Something I can fix with some setting?

I use Intrepid, but I saw this problem already in Breezy Badger.

---

### Post by Arndt on 2009-03-30
Has no one even encountered the phenomenon?

---

### Post by MihaiCapot&#259; on 2009-11-19
I have this problem in 8.04 and 9.10. And it's not only affecting gnome-terminal, but pidgin and empathy as well.
I reported the bug at Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/452313](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/452313)
I also found this old Debian bug report:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=240271](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=240271)

---

### Post by Arndt on 2009-11-19
> **MihaiCapot&#259 said:**
> I have this problem in 8.04 and 9.10. And it's not only affecting gnome-terminal, but pidgin and empathy as well.
I reported the bug at Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/452313](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/452313)
I also found this old Debian bug report:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=240271](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=240271)

9.10 also? I think I haven't noticed the problem since I upgraded to 9.04, and now to 9.10. I looked at the source code to gnome-terminal and tried to determine what was happening, and only found out that there is plenty of dead or completely bogus code in there, not getting closer to the problem.

For me, a window now keeps focus when the mouse is moved outside it, as long as it doesn't go inside some other window, but only one cursor is blinking at a time.

---

### Post by MihaiCapot&#259; on 2010-05-11
For me, [Unclutter]("http://ubuntuforums.org/showthread.php?t=394825") is causing this. Starting Unclutter with the -noevents option is a workaround.

A better description of my problem: when hovering the cursor over a text input widget of a not-focused window, a cursor will start blinking in that widget when the Unclutter timeout expires.

---

