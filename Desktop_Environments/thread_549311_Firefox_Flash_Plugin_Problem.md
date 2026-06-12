---
title: "Firefox Flash Plugin Problem"
date: 2007-09-12
forum: Desktop Environments
---

### Post by Tony Amidei on 2007-09-12
I have two observations that seem to be stopping me from completing the task of installing a plugin for Firefox.  I have Xubuntu 7.04 and I am attempting to install Flash Player.

1. When i attempt to open Terminal (Applications -> Accessories -> Terminal) on my computer the screen flashes what looks like the Terminal application and then it goes away and a Xubuntu login box pops up asking for name then password.

2. Next after this did not work i attempted to drag and drop the libflashplayer.so file into the /use/lib/mozilla-firefox folder. It would not work (dragged and dropped it but it did not move over) but i did notice that this folders 'permissions' are set to 'root'.

I refered to these sites so far: 
http://www.softonaut.com/2007/02/07/adobe-flash-player-9-for-linux-as-firefox-plugin/  
http://plugindoc.mozdev.org/faqs/firefox-linux.html

Could someone make some sense of this to me?

:(

---

### Post by Misosaki on 2007-09-12
Hi,

Not sure about 1), but for 2), you'll need root access to drop files into the plugins folder, so the easiest way would be via Terminal, and typing e.g. 

```

sudo mv libflashplayer.so /usr/lib/mozilla-firefox/plugins

```

Assuming you're already in the place where you have libflashplayer.so. If not, go the directory where it is first, e.g. cd Desktop (if it's on your desktop).

Hope that helps a little. Good luck!

---

