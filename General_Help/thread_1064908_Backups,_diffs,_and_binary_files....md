---
title: "Backups, diffs, and binary files..."
date: 2009-02-09
forum: General Help
---

### Post by Cadmus on 2009-02-09
I'm trying to come up with a good way to back up my Vista/Hardy machine.

I have a large home server (Hardy) with plenty of free space, but not enough for more than one (perhaps two) full backup(s) of my HD so I was thinking of using diffs to keep one 'Master Copy' of my HD (say once a month) and diffs from then on in.

What programs/uilities/commands can be used (prom a liveCD or liveUSB) to produce a diff between two binary files, which can then be merged so if I do need to restore I get some flexibility. I know about the diff command and it's ilk, but I've been unsuccessful finding how to do all the same with binary files.

I don't fear much from the command line, in fact it would be preferred so I get more of an understanding of what's happening, also it keeps the whole thing more portable.

Can someone point me in the right direction?

---

### Post by Cadmus on 2009-02-09
Well a bit of rummaging has found me xdelta, which could be what I'm looking for, especially as it seems to play well with piping, which would make it possible to compress the inital image and save myself some space.

---

### Post by snova on 2009-02-09
Perhaps look at rsync? I don't know how well it fares on disk images (which it sounds like you're trying to do), but it efficiently keeps one set of files updated according to the other, sending only deltas between the client and server.

---

### Post by unutbu on 2009-02-09
```
rsync -a /home/user/ /backup/user/
```

would make a full copy of all files and directories in /home/user/ to /backup/user/.
```

rsync -a --compare-dest=/backup/user/ /home/user/ /backup/user_diffs/
```

would compare the files in /home/user/ to the files in /backup/user/ and copy only those files which have changed or which are in /home/user/ but not in /backup/user/ to /backup/user_diffs/.

---

### Post by Cadmus on 2009-02-10
Rsync is the mutt's nut's, I use it an awful lot. But it works on a file level, the reason why (given the choice) I'd rather work on the device level is it's a 100% backup, no need to worry about whether or not the right directories are backed up or if a restore is hampered by some arcane file nestled deep in a file system.

Looking more at xdelta I've started to get a plan together:

[LIST=1]
[*]Boot from LiveCD
[*]Install xdelta (if it's not already on there)
[*]Mount remote directory through sshfs/samba
[*]'dd if=/dev/sda of=/remote/mount/point/20080210.img'
[*]'xdelta3 -s /remote/mount/point/20080210.img /dev/sda /remote/mount/point/20080310.x3d'
[/LIST]

Things to do include checking a diff, x3d might play ok with piping into cmp so the reult of the old image merged with the diff can be compared to the drive.

Then when diffs need getting rid of they can just be merged into the disk image, obviously on a 500GB drive this could become a bit of a slow operation, at least the merging can be done on the server in slower time.

---

