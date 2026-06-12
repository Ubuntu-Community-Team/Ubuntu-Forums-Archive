---
title: "rTorrent automatical move completed files"
date: 2009-03-15
forum: General Help
---

### Post by smeerbartje on 2009-03-15
I have read a ton on topics regarding the function which allows us to automatically move completed torrents but I still have something configured wrong in my rtorrent config file. Here it is:

```

# Default directory to save the downloaded torrents.
directory = /home/rogier/downloads/incomplete

# Default session directory.
session = /home/rogier/downloads/session

# Watch a directory for new torrents, and stop those that have been deleted.
schedule = watch_directory,5,5,load_start=/home/rogier/downloads/torrent/*.torrent
schedule = untied_directory,5,5,stop_untied=
schedule = untied_directory,5,5,close_untied=
schedule = untied_directory,5,5,remove_untied=

# Stops uploading when ratio is 2.0
schedule = ratio,60,60,"stop_on_ratio=200"

# Move completed torrents
on_finished = move_complete,"execute=mv,$d.get_base_path=,/home/rogier/downloads/complete/;d.set_directory=/home/rogier$

port_range = 50000-50100

```

The problem is that the completed torrents (when at target ratio) are not moved to the completed directory. What am I doing wrong?

---

### Post by fatbotgw on 2009-03-15
You have a comma (,) right after "get_base_path=" but before the location.  Try taking it out and see what happens.

---

### Post by smeerbartje on 2009-03-16
> **fatbotgw said:**
> You have a comma (,) right after "get_base_path=" but before the location.  Try taking it out and see what happens.
I have changed the on_finished rule to this one:

```

on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/rogier/downloads/complete"

```

Now it's working correctly. When a torrent has finished downloading, the files are being copied the the 'complete' directory. But I still want an extra function:

When the ratio is reached (and the torrent has been downloaded 100%), I want the torrents to be deleted from rTorrent. Do you think this is possible?

---

### Post by fatbotgw on 2009-03-16
I'm not sure if it will do that.  If it can it will be in in the man pages:  man rtorrent

---

### Post by smeerbartje on 2009-03-17
> **fatbotgw said:**
> I'm not sure if it will do that.  If it can it will be in in the man pages:  man rtorrent

Cool, thanks, I will have a look at it.

---

### Post by hyper_ch on 2009-03-17
what version of rtorrent? the command changed from 0.8.3 to 0.8.4

---

### Post by smeerbartje on 2009-03-17
> **hyper_ch said:**
> what version of rtorrent? the command changed from 0.8.3 to 0.8.4

Actually I don't know and I'm unable to check now (since I'm at work, not forwarded SSH port). I did a "sudo apt-get install rtorrent"... so which version will apt then install?

---

### Post by hyper_ch on 2009-03-17
a very old version... not sure if it's already 0.8 or still 0.7

---

### Post by smeerbartje on 2009-03-17
I have installed new version now manually, I will try if this version does what I want.

---

