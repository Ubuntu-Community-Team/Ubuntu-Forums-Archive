---
title: "System Sound Problems"
date: 2005-03-31
forum: Desktop Environments
---

### Post by gaza on 2005-03-31
Ok, here's my description of what's going on with my computer.

First I couldn't listen to any sounds at all. And I had no volume controll elements. Neither ubuntu sounds nor mp3's or other stuff would play.

Today some friends that use linux all the time helped me get my alsa configuration up and running. And, as far as I can tell, all mp3, movie sounds and stuff like that are working ok. But, for all of this to work, I had to "deselect" the "enable sound server from startup" in my Sound preferences.

And so now I have no ubuntu sounds.
**How can I tell Gnome to use alsa instead of esd??**

Is it possible? I don't know about these things, so if you can help me I'll be thankfull.

 :razz:

---

### Post by ykpaiha on 2005-03-31
This is not an answer sorry.
But this occure to me as well and after 1hour and a half without sound, I installed Kubuntu.!!! 
AS funny as it is there was sounds after that in gnome desktop (§/;:!!:!!:;,,;:ùmlù).

Now if I want sounds I first use kde, then gnome, odd, stange but true. :?:  :?:

---

### Post by chronusdark on 2005-03-31
you need to setup software mixing for alsa
check this out...[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)
it worked for me
i also had to delete my .esd_auth to get esd to work properly

---

