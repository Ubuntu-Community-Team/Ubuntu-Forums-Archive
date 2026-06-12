---
title: "Mount / link multiple folders to one"
date: 2010-12-23
forum: Desktop Environments
---

### Post by kkaldroma on 2010-12-23
I have 3 disks on my (Ubuntu 10.04 server) NAS box that contain all of my old compressed recorded television for playback on my MC7 box.

Currently I have to mount all three disks separately and remember what is where. 
Is there a way to either mount the three disks into one, or permanently link all three disks into one mountable (samba) location?

I would like all of my files to be in one location not linked sub folders in one mount
i.e.  
(mount ->link disk 1 -> disk 1 folders
           ->link disk 2 -> disk 2 folders
           ->link disk 3 -> disk 3 folders)
I want
(mount ->folders from disk 1/2/3)

---

### Post by roguebuck on 2010-12-23
Im curious about this, too. Ive tried setting multiple --bind entries in fstab, but that effectively only binds the last --bind entry, as im assuming it re-binds the folder each time it comes across an entry. 

I have a similar setup, where i have videos spanned across 3 drives that id like to show up in one ~/Videos folder

---

### Post by kkaldroma on 2010-12-24
I tried writing a script to use 'ln -s' links into one of the disks but for some reason MC7 took FOREVER to load the folder and it would fail to load files through the symbolic link too often for it to be a viable option.

Between your bind (@roguebuck) and my link / fstab, I am S.O.L on ideas.

I know it is possible on one end or the other (my Video_TS files from 3 different disks load to the same menu in MC7) but I don't want to program anything in C# on the WINminefield side to get things going.

help me UbuCommunity, your my only hope.
       (gee,  I hope my geek reference will make the gurus come out and hand me the answer ::he says in his inner monologue:: )

---

### Post by luvshines on 2010-12-25
> **roguebuck said:**
> Im curious about this, too. Ive tried setting multiple --bind entries in fstab, but that effectively only binds the last --bind entry, as im assuming it re-binds the folder each time it comes across an entry. 

I have a similar setup, where i have videos spanned across 3 drives that id like to show up in one ~/Videos folder

For this kind of setup, I mount --bind all my directories under one parent directory and share the parent directory. Then mount that parent directory on the client machine

Eg.
mount --bind /video1 /parent/video1
mount --bind /video2 /parent/video2
...

mount -t cifs //server-ip/parent ..

---

### Post by kkaldroma on 2010-12-25
luvshines
> 
mount --bind /video1 /parent/video1
mount --bind /video2 /parent/video2


This just mounts one directory over the other, not two into one.
Are you running a special or updated version of Bind?

---

### Post by kkaldroma on 2010-12-25
Got it.

unionfs-fuse 

use:
unionfs-fuse /folder/1=RW:/folder/2=RW /mount/point


Still not happy being mounted by windows but I'll figure it out.

---

### Post by kkaldroma on 2010-12-28
Windows still has a "permission" error when trying to mount a fused folder as a share.
If anyone knows how to fix this please let me know

The mount multiple folders into one issue has been resolved so I am marking the thread as Solved.

---

