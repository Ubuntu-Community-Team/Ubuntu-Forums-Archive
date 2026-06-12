---
title: "amaroK won't play MP3"
date: 2005-12-11
forum: General Help
---

### Post by Thunk on 2005-12-11
I recently installed amaroK via "Add Applications" and it looks like a great WinAmp alternative. It wouldn't, however, play MP3 files.
amaroK's website claims that it supports MP3 and that I don't have the appropriate decoders. It only provides a solution for RedHat users.

Does anybody have a good solution for this?

---

### Post by DaMasta on 2005-12-11
Change the engine to xine. Make sure you have gstreamer0.8-xine installed.

---

### Post by DiscoKiller on 2005-12-11
had the same problem....consult my post
[http://www.ubuntuforums.org/showthread.php?p=558378#post558378](http://www.ubuntuforums.org/showthread.php?p=558378#post558378)

---

### Post by kaamos on 2005-12-11
- Enable universe and multiverse repositories in /etc/apt/sources.list
- run command: sudo apt-get update
- run command: sudo apt-get install gstreamer0.8-plugins-multiverse
- run command: gst-register-0.8

Hope this helps.

---

### Post by Thunk on 2005-12-11
I updated all the gstreamer plugins, and also installed amarok-xine through Synaptic, but I still can't see the xine engine. Should I restart my terminal? The only engines I can see are the ones that end with "sink"...

Any suggestions?

I was looking in the wrong place ](*,)  Now it's working flawlessly (w/ xine engine).

Thanks!

---

### Post by renis-pinkles on 2007-11-17
> **kaamos said:**
> - Enable universe and multiverse repositories in /etc/apt/sources.list
- run command: sudo apt-get update
- run command: sudo apt-get install gstreamer0.8-plugins-multiverse
- run command: gst-register-0.8

Hope this helps.
i tried your respons, however, after entering sudo apt-get install gstreamer0.8-plugins-multiverse it said "E: Couldn't find package gstreamer0.8-plugins-multiverse" 

Any suggestions?

---

