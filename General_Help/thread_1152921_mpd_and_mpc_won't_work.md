---
title: "mpd and mpc won't work"
date: 2009-05-08
forum: General Help
---

### Post by jens1245 on 2009-05-08
I am trying to get MPC and MPD to work. I succesfully installed both. First i got an error that the MPD_PORT and MPD_HOST weren't set. I figured out I had to do export MPD_PORT=6600 and export MPD_HOST=6600.

Now it seemed like MPC worked.
I let MPD build a database
Updated MPC
Added files to Playlist
And tried MPC play, but nothing happens.

Conky gives this error:Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

My mpd.conf:

music_directory		"/home/jens/Desktop/Music"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
pid_file		"/var/run/mpd/pid"

bind_to_address                 "127.0.0.1"
port                            "6600"

Thanks in advance!

---

