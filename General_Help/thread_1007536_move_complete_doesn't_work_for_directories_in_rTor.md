---
title: "move_complete doesn't work for directories in rTorrent"
date: 2008-12-10
forum: General Help
---

### Post by Sakartu on 2008-12-10
Hey guys,
I've been wrestling with my .rtorrentrc for a couple of hours now, but I can't seem to get it working. What I want is:

-To add a couple of watches to directories for torrents in a specific category
-To move a completed torrent from the general download dir to the specific dir for that category

I've tried the example file and also the tutorial located [-->here<--]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrentstodifferentdirectorydependingonwatchdirectory") but I seem to get the same error over and over: "Download event action failed: Bad return code." Is there something wrong in my syntax or is something else wrong? The relevant parts in my .rtorrentrc are:

```
# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory_1,5,5,"load_start=/media/bin1/Torrents/Films/*.torrent,d.set_custom1=/media/media/Downloads/Films/"
schedule = watch_directory_2,5,5,"load_start=/media/bin1/Torrents/Frodo/*.torrent,d.set_custom1=/media/bin1/Incoming/Frodo/"
schedule = watch_directory_4,5,5,"load_start=/media/bin1/Torrents/Series/*.torrent,d.set_custom1=/media/media/Downloads/Series/"
schedule = watch_directory_5,5,5,"load_start=/media/bin1/Torrents/Other/*.torrent,d.set_custom1=/media/bin1/Incoming/"

# on a stop, move the download to the dir in $d.set_custom1 and start sharing from that dir
on_finished = move_complete,"d.set_directory=$d.get_custom1= ;execute=mv, $d.get_base_path=, $d.get_custom1="
```

I've tried moving the spaces around a bit, but I don't think that should matter too much... I've also already tried not to set the new directory (with d.set_directory), but that just crashes rTorrent. I've also moved the set_directory command to behind the mv command, after which it doesn't do anything anymore. The weirdest thing is, it works perfectly fine for torrents with just files in them, but doesn't work for entire directories.. Think it has something to do with permissions?

Has anybody got a clue what I'm doing wrong?

---

