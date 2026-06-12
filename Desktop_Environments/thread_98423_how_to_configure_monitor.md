---
title: "how to configure monitor"
date: 2005-12-03
forum: Desktop Environments
---

### Post by mert on 2005-12-03
I just installed ubuntu on an old macintosh (beige G3).  The system is up and running but the monitor refresh rate is slower than it should be.  The screen resolution tool won't let me select a faster refresh rate at this resolution (1024x768).  I'm guessing that X is configured with a generic monitor (or the wrong monitor) sync rates or some such thing.  Is there a graphical (or text) tool to let me select my monitor type (viewsonic A70) from a list?  Or, do I have to edit the xorg.conf file manually?  Thanks!
Mike

---

### Post by teaker1s on 2005-12-03
sudo dpkg-reconfigure xserver-xorg
you will need to know horisontal sync and vertical refresh rates for monitor
video memory is mb x 1024 if there is seperate graphics

---

### Post by KermitJr on 2005-12-03
Make SURE you put the video memory amount in even though the configurator says you can skip it.  I've had problems a few times without it if I had a non-detected monitor.

KJ

---

### Post by teaker1s on 2005-12-03
look[here]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21") after the first command in previous post

---

### Post by mert on 2005-12-03
Wow, those were fast replys!  Thanks!  How can I switch to text-based login instead of a graphical login?  If I screw up my xorg.conf file I'd like to be able to have shell access to put back the original file.  In redhat based systems I could switch runlevels in inittab.  Does it work the same way in ubuntu?  If so, which runlevel would I use as default? 
thanks again
Mike

---

