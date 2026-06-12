---
title: "rTorrent automatic stop/remove/move torrents"
date: 2009-03-10
forum: General Help
---

### Post by smeerbartje on 2009-03-10
I have installed rTorrent on my 8.04 server; it's working perfect! Now I would like to fine-tune by using the .rtorrent.rc file. What I want is this:

[LIST]
[*]Scan directory for new .torrent files
[*]Download (partial completed) torrents to /home/user/downloads/incomplete
[*]Once completed, the data must be moved to /home/user/downloads/complete and keeps seeding until 150%
[*]When ratio of 150% is reached, remove torrent from rTorrent
[/LIST]

I think this all is possible, but I can't manage to do this. Please have a look at my config file below. The 'watch'-dir. is working perfect. After copying a file into the directory, rTorrents starts downloading. But the automatic moving function does not work. What am I doing wrong?

```

# Default directory to save the downloaded torrents.
directory = /home/smeerbartje/downloads/incomplete

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/smeerbartje/downloads/torrent/*.torrent
schedule = untied_directory,5,5,stop_untied=      ??? what to put here ???

# Session directory
session = /home/smeerbartje/downloads/session

# Move completed torrents
on_finished = move_complete,"d.set_directory=/home/smeerbartje/downloads/incomplete/;execute=mv,-u,$d.get_base_path=,/home/smeerbartje/downloads/complete/"


# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

```

---

### Post by brujoand on 2009-03-10
Try to change this:
```

on_finished = move_complete,"d.set_directory=/home/smeerbartje/downloads/incomplete/;execute=mv,-u,$d.get_base_path=,/home/smeerbartje/downloads/complete/"

```
To this

```

on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/smeerbartje/downloads/complete/;d.set_directory=/home/smeerbartj/downloads/complete/"

```

I find it very confusing that there are now two pointers to the completed folder, but this works for me. 

Anders

---

### Post by smeerbartje on 2009-03-10
> **GrimmVarg said:**
> Try to change this:
```

on_finished = move_complete,"d.set_directory=/home/smeerbartje/downloads/incomplete/;execute=mv,-u,$d.get_base_path=,/home/smeerbartje/downloads/complete/"

```
To this

```

on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/smeerbartje/downloads/complete/;d.set_directory=/home/smeerbartj/downloads/complete/"

```

I find it very confusing that there are now two pointers to the completed folder, but this works for me. 

Anders

I tried your suggestion, but unfortunately it didn't work. It receive error messages at the bottom line of rTorrent saying: "Download event action failed: Bad return code.". Can you tell me how to interpretate the on_finished event?

---

### Post by gymmarn on 2010-01-30
Dunno if this is still a problem but as I found it via google so I'll respond for future readers.

With rtorrent 0.8.4 and beyond all these commands have changed.

> **smeerbartje said:**
> I have installed rTorrent on my 8.04 server; it's working perfect! Now I would like to fine-tune by using the .rtorrent.rc file. What I want is this:

[LIST]
[*]Scan directory for new .torrent files
[*]Download (partial completed) torrents to /home/user/downloads/incomplete
[*]Once completed, the data must be moved to /home/user/downloads/complete and keeps seeding until 150%
[*]When ratio of 150% is reached, remove torrent from rTorrent
[/LIST]

I think this all is possible, but I can't manage to do this. Please have a look at my config file below. The 'watch'-dir. is working perfect. After copying a file into the directory, rTorrents starts downloading. But the automatic moving function does not work. What am I doing wrong?

```

# Default directory to save the downloaded torrents.
directory = /home/smeerbartje/downloads/incomplete

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/smeerbartje/downloads/torrent/*.torrent
schedule = untied_directory,5,5,stop_untied=      ??? what to put here ???

# Session directory
session = /home/smeerbartje/downloads/session

# Move completed torrents
on_finished = move_complete,"d.set_directory=/home/smeerbartje/downloads/incomplete/;execute=mv,-u,$d.get_base_path=,/home/smeerbartje/downloads/complete/"


# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

```

#To watch a directory for new torrents:
schedule = watch_directory,10,10,"load_start=~/pathtotorrents/*.torrent"
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=

#Move files to folder Complete (change to fit)
system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,~/Complete;d.set_directory=~/Complete"

Stop on ratio is also changed with 0.8.4. New syntax is these three commands, only 1 is needed for what you want to achieve though:
#Stop torrents when reaching upload ratio 150 percent
ratio.enable=
ratio.min.set=150
#ratio.max.set=300
#ratio.upload.set=100M

Hope it helps. You can also pretty easily get rtorrent unpack your files and do other fun stuff. But what I haven't figured out yet is how to delete the rar files when reaching the specified ratio (I unpack everything after download so don't need them).

---

### Post by chalewa on 2010-02-27
I am reallllly struggling with this command

My ultimate goal is to move torrents based upon their tracker, and I am really close, but for some reason I cannot get this command to execute correctly. 

```
system.method.set_key = event.download.inserted_session,tracker,"d.set_custom2=$execute_capture={script.sh,$d.get_tied_to_file=}"
```


rtorrent throws this error:

```
 Download event action failed: Could not find closing '}'
```

---

### Post by pwn on 2010-06-19
Try this:

```
system.method.set_key = event.download.inserted_session,tracker,"d.set_custom2=\"$execute_capture={script.sh,$d.get_tied_to_file=}\""
```

---

