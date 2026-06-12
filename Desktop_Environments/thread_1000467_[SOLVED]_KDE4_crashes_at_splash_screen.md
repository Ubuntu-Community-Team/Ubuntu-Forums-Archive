---
title: "[SOLVED] KDE4 crashes at splash screen"
date: 2008-12-02
forum: Desktop Environments
---

### Post by storm1277 on 2008-12-02
hi, I'm a linux/kubuntu newbie with a problem I can't seem to overcome.

After a weird instance of my kde desktop crashing to what I assumed was a gnome desktop, I found that I could remove all GNOME apps to have a 'pure' KDE environment - I did this after some forum searching....may not have been the best option upon reflection, but it stopped the desktop crashing at least :)

HOWEVER! I can no longer start my computer. KDE4 gets halfway through the splash screen (to the plamsa cashew icon) then the screen blanks out and I'm left with a black screen, but full control over the mouse pointer. It even seems to go to the screen saver after a while (which is blank for interests sake).

I'm stuck on how to fix it, even after trolling through the forums. Any suggestions?

---

### Post by storm1277 on 2008-12-03
> **storm1277 said:**
> hi, I'm a linux/kubuntu newbie with a problem I can't seem to overcome.

After a weird instance of my kde desktop crashing to what I assumed was a gnome desktop, I found that I could remove all GNOME apps to have a 'pure' KDE environment - I did this after some forum searching....may not have been the best option upon reflection, but it stopped the desktop crashing at least :)

HOWEVER! I can no longer start my computer. KDE4 gets halfway through the splash screen (to the plamsa cashew icon) then the screen blanks out and I'm left with a black screen, but full control over the mouse pointer. It even seems to go to the screen saver after a while (which is blank for interests sake).

I'm stuck on how to fix it, even after trolling through the forums. Any suggestions?

I have since fixed this problem following the guidelines in this post: [http://ubuntuforums.org/showthread.php?t=677588T]("http://http://ubuntuforums.org/showthread.php?t=677588T") in particular the following code lines:

> *sudo apt-get pruge kdelibs5*
Followed by reinstalling KDM and typing > *sudo dpkg-reconfigure kdm* as suggested by another thread: [http://ubuntuforums.org/showthread.php?t=874503]("http://ubuntuforums.org/showthread.php?t=874503")

I then was able to boot into GNOME where I could reinstall kubuntu-desktop
*sudo apt-get install kubuntu-desktop*

Basically I've removed and reinstalled KDE4 - I didn't find a 'quick fix' but this worked wonders for me.

---

### Post by rudihawk on 2008-12-03
Glad you solved your problem man! :)

---

