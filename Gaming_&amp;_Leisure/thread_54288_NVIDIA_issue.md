---
title: "NVIDIA issue"
date: 2005-08-04
forum: Gaming &amp; Leisure
---

### Post by trivialpackets on 2005-08-04
Anyone have any ideas as to why when I play games, such as frozen bubble, or battle for wesnoth, that I get a black screen down the right side of my screen?  It's only when a game goes in full screen mode that this is an issue.  I'm not sure, as I had Hoary installed once before, and it worked fine, but now it's doing it.  I've got an NVIDIA card installed, Not sure where to turn, going to install a light weight manager, just to see what that does, but looking for a direction.

---

### Post by corruption on 2005-08-04
have you installed the nvidia-glx package? a quick "sudo apt-get install nvidia-glx" may solve your problem in a matter of seconds.. just a thought!

---

### Post by trivialpackets on 2005-08-04
[QUOTE=corruption]have you installed the nvidia-glx package? a quick "sudo apt-get install nvidia-glx" may solve your problem in a matter of seconds.. just a thought![/QUOTE]
 Yeah, the problem started when I got the Nvidia drivers installed and set up "properly" although I use that term lightly.  The things seem to be working fine, aside from this.  Frustrating to say the least, as I had it configured properly once before.

---

### Post by corruption on 2005-08-09
Did you apt-get the drivers, or did you install from the official nvidia package? I had some funky issues when trying the official nvidia packages (xorg not remembering its configuration after a reboot, games coming up in 1280x1024, but showing in an 800x600 window, etc) and they were all solved by going back to the ubuntu drivers.

---

### Post by rafakl on 2005-09-04
For me, the problems where solved when i installed the nvidia drivers from the repositories (apt-get install nvidia etc etc).

The original ubuntu drivers lacked 3d acceleration.

---

