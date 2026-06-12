---
title: "[SOLVED] Deluge torrent client running without login"
date: 2008-12-21
forum: General Help
---

### Post by Kissell on 2008-12-21
I'm using the deluge bit torrent client... it's great, but, when I reboot the server it waits at the login screen, if nobody logs in then deluge never starts...  :(

I want to be able to drop .torrent files into a folder on the server and have it automatically download, that works, if someone is logged in...  and I don't want to have the server automatically login then have the user lock the screen...  I also don't want to switch to a different client because I like this one and I have a bunch of RSS feeds setup in it to automatically download...

Can anyone tell me if there's a way to have deluge run without having anyone login?

---

### Post by Kissell on 2008-12-23
The version of deluge that comes with the ubuntu default repositories is very old...  I installed the new version of deluge which allows me to launch it as a daemon, so it will load before anyone logs in...

Unfortunately the new version didn't come with any FlexRSS plugin, so I had to hack that with help of the deluge forums and got it to work, but I did have to rebuild my RSS feeds...  the old flexrss.dat wouldn't import to the new version.  :(

But, it is all working the way I want now.  
:guitar:

---

