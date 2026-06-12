---
title: "[SOLVED] Graphical Troubles on Dell Inspiron 1420n"
date: 2007-07-30
forum: Dell  Ubuntu Support
---

### Post by ghindo on 2007-07-30
I have an Inspiron 1420n notebook and have been loving it, save for a couple of things - one, Compiz causes the computer to freeze up completely; and two, the screensaver causes the computer to freeze up completely.  I suspect that these two issues are related, but I'm not sure what to do about it.  Any help?

**EDIT:**  Solved my problem with help from [this thread]("http://ubuntuforums.org/showthread.php?t=506744").  Thanks for the help, guys!

---

### Post by Syke on 2007-07-30
This is a common problem. The x3100 video driver just isn't stable in Feisty. I'm somewhat surprised that Dell would ship a laptop with bad drivers.

Two solutions:

1. Don't do 3D. That means no Compiz, no 3D games, no 3D screensavers.

2. Wait for Gutsy. The x3100 driver should be solid by the time Gutsy is released.

---

### Post by notwen on 2007-07-30
Have you checked out this [thread]("http://ubuntuforums.org/showthread.php?t=506744")?  It seems they can enable Compiz(original Compiz) and/or Beryl w/o issues after installing a couple of updated intel packages.  If you do try it, please let me know if it works as I should be getting my 1420n in sometimes mid-August. =]

---

### Post by Paul S on 2007-07-30
You may also want to upgrade your compiz to compiz-fusion via Trevino's repository.  There's been a lot of work on compiz to fix a lot of but, plus the new plugins (expo + shift switcher) are better than the cube!

regards,

---

### Post by sciurus on 2007-08-01
I'm successfully using the intel drivers and xrandr from Gutsy plus Compiz-Fusion.

---

### Post by notwen on 2007-08-02
Update. =]

Recieved my Dellbuntu Inspiron 1420n yesterday. I got Beryl working on it simply by enabling "Pre-Released Updates" in System->Administration->Software Sources->Updates and then running the Update Manager. Installed Beryl using this guide. Haven't gotten a chance to play w/ all of Beryl's configs, but wobbly windows and 3d cube work w/o a hitch so far. The X3100 seems to be more than enough to run it smoothly. Once reports of Compiz-Fusion running on it start appearing then I'll give it a try. Anyone else having luck w/ the X3100 on the Insipron 1420n? =]

---

### Post by timseal on 2007-08-02
> **notwen said:**
> 
Installed Beryl using this guide. 

Which guide?

---

### Post by ghindo on 2007-08-02
> **timseal said:**
> Which guide?He copied that post from another one he made in [this thread]("http://ubuntuforums.org/showthread.php?t=506744"), which, incidentally, helped me solve the problem this thread is for.

---

### Post by apswartz on 2007-08-02
can you mark this thread as solved?

---

### Post by ghindo on 2007-08-03
Sorry, thought I had.

---

