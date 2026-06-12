---
title: "Xubuntu screen tearing not found in Ubuntu"
date: 2012-05-04
forum: Desktop Environments
---

### Post by sdpagent on 2012-05-04
Dear all, 
Can anyone tell me why and how to fix the fact that if I play a video in Xubuntu, there is significant screen-tearing when playing an hd video in vlc, not found when I play the same video in a ubuntu session? (Same computer, I just installed both desktops). 

I noticed this in the past when I had just a xubuntu install, but thought that it was just me, but now I have both desktops on the same machine I have 'proven' it to myself. The same settings are set in vlc media player with GPU acceleration on.

I have already tried turning off/on xfconf with no success: suggested here: [http://ubuntuforums.org/showthread.php?t=1926343](http://ubuntuforums.org/showthread.php?t=1926343)
TBH i dont like altering settings which I don't know what they do.

Stu

Example screenshot:
[IMG]http://img1.uploadscreenshot.com/images/main/5/12401590584.png[/IMG]

---

### Post by Timothy Benton on 2012-05-07
I don't believe Xfce is GPU accelerated. Installing Compiz over top of Xfce should fix your problem. Compiz is hardware accelerated and has an option for v-sync. However, using Compiz may degrade performance.

PS  Ubuntu comes with Compiz already installed.

---

### Post by Jose Catre-Vandis on 2012-05-07
AMD or NVidia GPU ?

My command line options for turning the Compositor on and off were simply to create a launcher for them. You can do the same through Settings Manager > Window Manager Tweaks

---

