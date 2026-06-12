---
title: "back up"
date: 2006-07-06
forum: Desktop Environments
---

### Post by recklessray on 2006-07-06
hi all,

bit of a noob - i have dapper running on my main pc and an xp box for all my midi/music apps. i have a shared ntfs drive on the xp box which i can see with samba no probs. i have a big empty drive to backup all the music on the shared ntfs drive but i need to know how to do it. i need it to syncronise basically. so when i add files to the ntfs drive, they will be 'backed up' to the ubuntu box at some regular point in time. 

also - and maybe this will be the same program??? - i like to copy the entire /home/ray directory from hda, the boot drive. to hdc - i use this command cp -uR /home/ray /media/hdc/backup/ ... which works a treat, but if i delete files on the source directory, they remain on the backup - which fills up with unwanted files.. is there a syncronisation program that could handle all this for me and make my life simpler?! any guidence / help will be most gratefuly received. im not a command line type - not yet, so any gui progs will be better i guess...

ray :)

---

### Post by mannheim on 2006-07-06
You can use rsync instead of cp. If you do:

```
rsync -av --delete /src/foo/ /dest/foo 
```

then rsync will copy all files from /src/foo/ into /dest/foo/, recursing into subdirectories and deleting files on the destination that no longer exist on the source. Only files that have changed will be copied. 

(If you previously used "cp" then the modification times of the copies will be different from the sources, causing rsync to copy everthing over again, the first time.)

The meaning of the flags to rsync are

```

  -a            archive mode (preserve timestamps symlinks etc)
  -v            verbose
  --delete      delete files on destination that are no longer on source

```

Type "man rsync" for more explanation and examples. Be **[COLOR="Red"]careful[/COLOR]** with --delete. If you have accidentally deleted 1000 songs from /src/foo and haven't noticed, then the --delete option will delete all the 1000 "backups" on  /dest/foo. To be safer, you can do

```
rsync -av --delete [COLOR="Red"]--backup --backup-dir=/dest/foobackup[/COLOR] /src/foo/ /dest/foo 
```

That will still delete the files from /dest/foo, but will place backup copies in /dest/foobackup. You can delete the backup when you are sure you haven't lost anything.

---

### Post by recklessray on 2006-07-06
great, and thanks for the indepth reply. i really apreciate that. ill install rsync and get cracking tonight.

best regards, ray

---

