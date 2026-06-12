---
title: "MPD playlists problems"
date: 2009-01-02
forum: General Help
---

### Post by perrti-y02 on 2009-01-02
Hello,
I am unable to find any way of getting any MPD client to be able to create edit or delete playlists. I am using a systemwide setup of MPD that has the config file at /etc/mpd.conf. The playlists folder is /data/playlists and music is found at /data/Music where /data is a whole hard drive with read write and execute permissions applied to everyone (by doing sudo chmod -R 777 /data).

Does anyone know of a solution to this?

I am running Ubuntu with the XFCE4 desktop (note that it wasn't installed as XUbuntu, don't know if that is significant)

---

### Post by mplexus on 2009-01-05
Can you connect to mpd?

Can you play files?

What user did you specify in /etc/mpd.conf?

---

### Post by mcduck on 2009-01-05
I have MPD running as user "mpd", and playlist directory configured to the default setting, /var/lib/mpd/playlists. Saving playlists works fine.

The playlists directory seems to be owned by user "mpd" and group "audio", permissions drwxr-xr-x.

This is pretty much out-of-the-box MPD setup, all the music is symlinked from my music directory to /var/lib/mpd/music and MPD is running as daemon.

---

### Post by mplexus on 2009-01-07
....

---

