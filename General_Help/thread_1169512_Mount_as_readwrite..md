---
title: "Mount as read/write."
date: 2009-05-25
forum: General Help
---

### Post by andrew-w on 2009-05-25
Hi, I am reasonably new to ubuntu(linux altogether)and I am having trouble mounting a partition that a normal user can read and write to.
My situation is this:

[LIST]
[*]I am dual booting windows xp and ubuntu 9.04
[*]I have a small fat32 partition to store my music on so both operating systems can access it
[*]I want to mount it in the place of my music directory
[/LIST]
the problem occurs on the last of these, if i mount in normally (by just accessing the drive or right clicking) so it comes up in /media/ it works all fine, read and write fine. BUT when i try: ```
sudo mount /dev/sda5 ./Music
``` it does replace the music folder in home but is read-only (unless accessed as root). so my question is how do i get this to have read/write access?
hope you can help me with this.

Andrew

---

### Post by regala on 2009-05-25
> **andrew-w said:**
> Hi, I am reasonably new to ubuntu(linux altogether)and I am having trouble mounting a partition that a normal user can read and write to.
My situation is this:

[LIST]
[*]I am dual booting windows xp and ubuntu 9.04
[*]I have a small fat32 partition to store my music on so both operating systems can access it
[*]I want to mount it in the place of my music directory
[/LIST]
the problem occurs on the last of these, if i mount in normally (by just accessing the drive or right clicking) so it comes up in /media/ it works all fine, read and write fine. BUT when i try: ```
sudo mount /dev/sda5 ./Music
``` it does replace the music folder in home but is read-only (unless accessed as root). so my question is how do i get this to have read/write access?
hope you can help me with this.

Andrew

are you sure it is mounted ro ? (type mount and post the output here)
by default when mounting a FAT32 partition, as Windows doesn't support Unix rights, should no option be given, all file/directories are supposed to belong to root. The cmdline you use, will only allow root to write on your drive. And no chown can change that.

Try mounting with:
```
 mount -o uid=<your_username> /dev/sda5 ./Music
```
it should work.

br, mathieu

---

### Post by andrew-w on 2009-05-25
Thanks that works, thank you. i knew it would be simple

---

