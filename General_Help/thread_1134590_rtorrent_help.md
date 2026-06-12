---
title: "rtorrent help"
date: 2009-04-23
forum: General Help
---

### Post by lmlypfan on 2009-04-23
I'm running a headless server, and using rtorrent to pull down live music.
I ssh into the server and start the torrent, then log out.
The next day i'd like to ssh back in and check the status of my torrents.
When i ssh back in and start rtorrent, none of my torrents are shown. I'm pretty sure they are still active by monitoring traffic on the WAN.

Thanks

---

### Post by nandemonai on 2009-04-23
You're closing rtorrent so no they wont still be running. rtorrent is not a daemon.

The only way I know to do this (which is what I do) is to run rtorrent in a screen session. That way you can detach the screen session, log out, log in later, reattach the screen session and viola.

```
man screen
```

---

### Post by lmlypfan on 2009-04-23
Thanks

Makes perfect sense

---

