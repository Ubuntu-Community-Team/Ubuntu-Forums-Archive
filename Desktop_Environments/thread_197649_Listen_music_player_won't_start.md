---
title: "Listen music player won't start"
date: 2006-06-16
forum: Desktop Environments
---

### Post by gosh on 2006-06-16
Hi everyone,

I installed Listen Music Player.
When I start it, it only shows the splash screen and then.... nothing :-(

When I start it from a terminal it says:

```
Traceback (most recent call last):
  File "/usr/bin/listen", line 409, in ?
    Listen()
  File "/usr/bin/listen", line 136, in __init__
    self.run()
  File "/usr/bin/listen", line 283, in run
    self.player.on_playlist_changed(self.player.current_song,False)
  File "/usr/lib/listen/player.py", line 502, in on_playlist_changed
    self.set_album_current_cover(False)
  File "/usr/lib/listen/player.py", line 539, in set_album_current_cover
    pixbuf = gtk.gdk.pixbuf_new_from_file_at_size(filename,75,75)
gobject.GError: Unrecognised image file format

```

---

### Post by MetalMusicAddict on 2006-06-17
How did you install it? Did you use their repo? Are you using 64bit?

---

### Post by gosh on 2006-06-18
Yes, I did.

I made it work by

apt-get remove ---purge listen
rm -r /home/username/.listen
apt-get install listen

funny, eh

---

