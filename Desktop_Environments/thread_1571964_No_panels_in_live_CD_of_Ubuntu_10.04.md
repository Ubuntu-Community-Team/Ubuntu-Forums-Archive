---
title: "No panels in live CD of Ubuntu 10.04"
date: 2010-09-10
forum: Desktop Environments
---

### Post by Ben_neB on 2010-09-10
I have a Dell Optiplex GX 150 running Ubuntu 9.10, which I am trying to upgrade to 10.04. However, when I boot onto the live CD, I get no panels. I have the background, and the icons, just no panel. I have tried the first two suggestions in [THIS]("http://ubuntuforums.org/showthread.php?t=840105") thread with no success. It doesn't do anything when I try the Ctrl+Alt+F1 suggestion, and typing in "gnome-panel" returns the error "cannot register panel shell: there is already one running". 

My specs are:

Pentium III 1ghz
512mb PC133 ram
Intel 82815 graphics.

I'm guessing that there is an incompatibility with my graphics card, although it works fine in 9.10. How high would the risk be of losing my panels if I just do an upgrade from 9.10 to 10.04 instead of using the live CD?

---

### Post by grief -l on 2010-09-10
try changing your screen resolution and fiddling with your monitor settings to bring them out of hiding

---

### Post by fatman65535 on 2010-09-10
I too have one of those machines, and I have run into the same problem.   This is an installation on my hard disk, from a Live CD.  After some serious googling, I found out the following:  For some reason, the install on my machine did not properly set up a "standard" account. In order to get Lucid to work, I had to either log in with a "failsafe GNOME" session (look at the bottom of your screen for that);   -or-  if I did login as a "normal GNOME" session, typing ALT-F2, and in the "run" box type: "pkill gnome-panel". Usually, after 15-30 seconds, the panels occur.  Now, if you think this is annoying, consider that on this same box, I have to juggle back and forth between Karmic, Lucid, Maverick (beta); and most unfortunately Windoze.  I would try the failsafe login first. The most irritating part is that I do not have one lick of a problem with Karmic. This popped up with Lucid; so obviously something got broke!

---

### Post by ld.4lpha on 2010-12-24
This problem occurred for me as well, although sporadically.  Sometimes the Live CD works flawlessly, while other times no panels load upon booting to the CD.

Killing the gnome-panel process as fatman suggested took care of the issue.



LD

---

### Post by fatman65535 on 2010-12-24
I am glad that my advice helped. If I may take the opportunity to point out, that the `breakage` of 10.04 over 9.10 is annoying, but, having more experience with 10.10 under my belt since the post, I must  reluctantly state that there is more `breakage` with 10.10.

Things that worked fine in 9.10 are broke on the exact same machine (thus eliminating HARDWARE differences). 10.10 has this annoying logout problem. Sometimes, IT DOESN'T, and leaves you hanging, forcing you to use the power button to get it to shutdown. You can try to shutdown through the terminal, (sudo shutdown -r now), but it does not always result in a complete power off. ARRRGGGGHHHH!

Lately, I have installed Kubuntu 11.04a1, and have had nothing but grief with it. I could not get any kind of menu to appear with KDE. Finally, I decided to try something - install GNOME!! Finally, I get a desktop with panels. But, still some of the same annoying problems, and authentication issues. In 10.10, I would run into some things (like software center) that does not prompt for a password, even it should. The only way to get them to work properly is to run them from the terminal as `sudo`.

All, I can say is this, a lot of thing worked fine in 9.10, and have been broken since. To me, that is not forward progress. I do not know if any of this is due to unanticipated consequences of attempts to `clean up the code`. All I can say is:** it is frustrating**!!!!

---

