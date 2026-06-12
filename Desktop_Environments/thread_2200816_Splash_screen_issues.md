---
title: "Splash screen issues"
date: 2014-01-21
forum: Desktop Environments
---

### Post by dave2001 on 2014-01-21
For 13.10, I did a fresh install of a base-system, then added KDE using "sudo-apt-get kde-plasma-desktop". In the past I've just used the Kubuntu distro, I don't know if this has anything to do with the following.

On boot, I get a tty login prompt for a several seconds before the kdm login starts.  Then, after login the system splash screen plays, halfway through the kdewallet pops up and then disappears a second or two later.. after you've had time to type one or two letters. The kdewallet then reappears after the splash screen animation ends and the desktop has finished loading.

These are not really "problems"... they do not interfere with functionality, I just find them a bit aesthetically irritating. They give boot-up an "unpolished" feel, and I do occasionally like to try and convert people to linux by showing them my laptop and letting them poke around and see what a great OS it is. For many people, visuals are a big first impression. 

Is there anyway I could go about skipping the brief display of the tty prompt (even if it's just with a blank/black screen)? Or a way to ensure kdewallet does not start and request a password until after the splash animation finishes? In case anyone asks I'm using the "minimalistic" splash screen from the default kde-plasma-desktop metapackage.

---

### Post by dave2001 on 2014-01-24
No kde gurus out there to give a suggestion?

---

### Post by marco-parillo on 2014-01-25
I can tell you on 'regular' Kubuntu (13.10 and Alpha2 for 14.04), I do not see this.
I also thought Kubuntu used Light DM, and not KDM.
You may want to try the #kubuntu IRC channel (you may need to try different times of day and night to catch the right expert);
Or [https://www.kubuntuforums.net/](https://www.kubuntuforums.net/) For example: [https://www.kubuntuforums.net/showthread.php?64352-Going-into-Terminal-window-when-booting-then-boots-into-Kubuntu](https://www.kubuntuforums.net/showthread.php?64352-Going-into-Terminal-window-when-booting-then-boots-into-Kubuntu)

But, if you do learn something, please come back here and post your results.

---

### Post by dave2001 on 2014-01-25
Yes, I figured that the Kubuntu version would have most little snags like this worked out. When I installed KDE it gave me an option at setup to choose LightDM or KDM. I chose KDM becuase that is what I thought I remembered using and liking in Kubuntu 12.04... but I could be remembering wrong.

Thanks for the links, it's been so long since I went to the Kubuntu forum, I forgot all about it.... now to see if I can remember my login info ;)

---

### Post by marco-parillo on 2014-01-26
You are very welcome. 
One other possibility: While reporting your bug on Launchpad may not help (because of your 'franken-distro'), maybe you can try: [https://bugs.kde.org/](https://bugs.kde.org/)
You can try to use kdm as your product, and do not be surprised if it changes as various people look at it.

---

