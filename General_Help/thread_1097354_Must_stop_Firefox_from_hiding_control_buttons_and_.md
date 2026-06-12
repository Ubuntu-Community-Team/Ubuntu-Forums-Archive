---
title: "Must stop Firefox from hiding control buttons and Linux taskbar"
date: 2009-03-15
forum: General Help
---

### Post by boothruwindow on 2009-03-15
Firefox has started hiding my taskbar, and my window control buttons have started disapearing after leaving a tab window open for a few minutes. I'm a bit of a control freak, so I want those buttons never to disappear unless I have a vid running full screan, and when I push the mouse to where the taskbar (or whatever you call the bar which displays open programs in Linux), I expect those processes to show - it's getting to be more annoying every time that I have to reach for the F11 key, so I need to stop it from doing this. I have used Firefox under Windows since it was first released, but have never seen it, nor any other program do something like this, so I find it a bit disturbing. It has always been my habit to leave browser windows maximized, so I wonder if someone got the bright idea that I may want the controls to disappear without my asking whenever the window is maximized, and implemented this so-thought cool trick just for the Firefox Linux version. Then again, I noticed an Ubuntu addon which I did not install myself, it must have been part of the CD package which contained the version of Firefox which I am running. 
Whatever it is, it must go - please help!

By the way, I just pulled up that add-on, called Ubuntu Firefox - apparently I could disable it if I dared (that may be interesting, sheeeeeeesh), but access to the Preferences is blocked. Should I do anything with this?

Thanks.

---

### Post by boothruwindow on 2009-03-16
:):)bump:):)

---

### Post by mb_webguy on 2009-03-16
To get rid of the Ubuntu Firefox add-ons, you have to uninstall the ubufox package (using Synaptic or apt-get).

As for the part about Firefox starting in full-screen, I've seen this complaint several times before (though I've never experienced it myself), and apparently it's a Compiz bug.  Look through your Compiz settings -- you may need to install the compizconfig-settings-manager package first -- and disable Legacy Fullscreen Support.

---

### Post by ubuntu27 on 2009-03-16
Hello boothruwindow.

I experienced the same problem with firefox before. I was able to fix the problem by following the tip from other members:

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=993013](http://ubuntuforums.org/showthread.php?t=993013)

---

### Post by boothruwindow on 2009-03-16
> **ubuntu27 said:**
> Hello boothruwindow.

I experienced the same problem with firefox before. I was able to fix the problem by following the tip from other members:

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=993013](http://ubuntuforums.org/showthread.php?t=993013)

Hey, that works! Thanks!

---

