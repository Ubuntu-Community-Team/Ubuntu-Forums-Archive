---
title: "America's Army and 5.10"
date: 2006-01-18
forum: Gaming &amp; Leisure
---

### Post by Human Geode on 2006-01-18
Just installed Ubuntu 5.10 on my desktop.  Niiiice.  It's taking a while, but I'm slowly adding in everything I need to survive.  Last night I finally got America's Army 2.50 running.  Thought I'd put my experiences here, maybe they will benefit someone else:

1.  First step was finding the Linux client... like running in circles.  Eventually found it here: [http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654](http://americasarmy.filefront.com/file/AASF_Direct_Action_v25_Linux_Full_Install;49654)

2.  Ran the installer, started armyops.  ERROR!  Something about libstdc++
     Solution:   sudo apt-get install libstdc++5-3.3-dev

3.  Next hurdle - WARNING: ALC_EXT_capture is subject to change
     Solution:  first of all, where to start?  I searched for Ubuntu and America's Army
    with the error message... but couldn't find what I was looking for.  Eventually, I just searched Google for "WARNING: ALC_EXT" and found that it was a video driver problem... so what next?  I found the following great tutorial for upgrading my Nvidia drivers: [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

4.  Gettin close here:  started it up, and... nope! no worky.  The error message was: Servname not supported for ai socktype
     Solution:  rm ~/.ICEauthority

5.  ran armyops ... and Success!!!

Hope this helps someone else.  Thanks to all who posted, and to tseliot for the NVidia driver upgrade tutorial.  I'm a midget standing on the toes of giants. ;)

---

### Post by Azion on 2006-01-19
Nice post, alot of people are having trouble with it, I luckily got mine to run no prob.

---

### Post by jon_z on 2006-01-20
It's crucial if your going to play a 3d game to make sure you install your 3d card drivers (Nvidia/ATI) because they dont automatically get installed..  Good job, if you like america's army, I suggest:[True Combat: Elite]("http://ubuntuforums.org/showthread.php?t=78674&highlight=TC%3AE")  It's a much more realistic Counter-Strike and its also a Linux Native!!

---

### Post by txgunslinger on 2006-01-20
Hmmm, maybe the 3d drivers are the cause of my problems.....it's amazing what you find just surfing the forums :)

---

