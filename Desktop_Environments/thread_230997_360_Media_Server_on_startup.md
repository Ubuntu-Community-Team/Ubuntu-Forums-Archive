---
title: "360 Media Server on startup?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Goonbridge on 2006-08-06
Hi,

I'm trying to setup 360 Media Server (a Linux variant of Windows Media Connect). The application itself seems to work fine, but I am looking for the best way to run it on startup (hopefully later versions will support this).

After searching around the forums a bit, it seems the easiest way to get this program running on startup would be to add the command I use to run the software, into the Preferences > Sessions application. The problem I am having is that 360 media server will not start as it seems to get confused about the path. When I normally run this program I change to the directory, then run it by using 'sh start'. When using Sessions I tried the command 'sh /mnt/storage/x360mediaserve/start', using the command on the Terminal spits out various errors, which I assume is the key to my problem.

How do I specify the path in the Sessions dialog? Is there a better (safer?) way to run this program?

Many thanks.

---

### Post by BitTorrentBuddha on 2006-08-06
Well, if it's an error resulting in being in the wrong directory, you could make the command ```
cd /mnt/storage/x360mediaserve/ && ./start
``` But I believe it has something to do with things not being mounted. 

PS I had no idea such an application existed, I'll make sure to look into this, thanks! :D

---

### Post by Goonbridge on 2006-08-07
Still no go, I don't think its a mounting issue as I can read / write files fine to that drive. :confused:

---

