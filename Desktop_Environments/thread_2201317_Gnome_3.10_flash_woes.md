---
title: "Gnome 3.10 flash woes"
date: 2014-01-23
forum: Desktop Environments
---

### Post by Richard_Romick on 2014-01-23
I installed Gnome 3.10 on my Ubuntu 13.10 desktop and really like it.  The only issue I have run into is maximizing flash videos will result in the video stopping and the screen going blank.  I have seen some websites detailing the bug from early 2013, but I didn't find a solution.  Any help would be appreciated.

---

### Post by mikewhatever on 2014-01-23
Who said there is a solution? Flash will never work well on Linux, it's time to accept it and move on.

---

### Post by Richard_Romick on 2014-01-25
It seems to be a problem specifically for Gnome as it worked fine in Unity.  It isn't enough to get me to change back on it's own, since flash is dying (I hope), but there are still some websites that use it.  Is there an alternative to websites that don't run HTML 5?

---

### Post by monkeybrain20122 on 2014-01-25
> **Richard_Romick said:**
> It seems to be a problem specifically for Gnome as it worked fine in Unity.  It isn't enough to get me to change back on it's own, since flash is dying (I hope), but there are still some websites that use it.  Is there an alternative to websites that don't run HTML 5?

Which websites? For some there are alternatives for other there aren't. There is a greasemonkey script that play flash videos in Totem and/or gnome-mplayer (via gecko-mediaplayer) for some popular sites (Youtube, Vimeo, Dailymotion ..)

[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

There is another, it doesn't work as well on Youtube (because google keeps changing things) but works on many random sites that are not even explicitly supported (it detects flash and replaces it dynamically) the catch is that if you hit a site of many flash objects it may freeze the browser(so the problematic sites needed to be blacklisted in greasemonkey, facebook is a well known one)

[http://linternamagica.org/](http://linternamagica.org/)

For firefox to use html5 player for some sites (e.g vimeo) gstreamer needed to be enabled because of h264 requirement. I have enabled it manually back in FF 24 or 25 (about:config --> media.gstreamter.enabled=true) I don't know if it is enabled by default now.

For Youtube there are many options. Aside from the scripts above there is also minitube, the updated-version (2.1.5) can be installed from the Software Centre (the one in the standard multiverse/universe repo is outdated). Smplayer also has a Youtube player but t doesn't play some channels (minitube does) There is also a vlc Youtube addon for Firefox (never used it though)

---

