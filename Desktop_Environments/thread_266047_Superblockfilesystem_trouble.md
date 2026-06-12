---
title: "Superblock/filesystem trouble"
date: 2006-09-26
forum: Desktop Environments
---

### Post by mipstien on 2006-09-26
Earlier today i was getting a Superblock error, that has gone away now but it still isn't 'checking file the filesystem's correctly. I run e2fsck or fsck with -f -c or anything really and i get 

/dev/sda7: 212490/13271040 files (2.5% non-contiguous), 11698428/26515274 blocks

when i first boot right now i get /dev/sda7 mounted can not check filesystem
check manually
or something very close to that.
if i press control+D which it tells me to do if i just want to skip checking it loads up into my ubuntu install and everything works fine. i have reloaded old superblocks already and that didn't change the error.
this started earlier today when i tried to resize my partition larger and it stopped working after that....it did resize most if not all of it i think?  

any help would be appreciated i have searched and searched and can't come up with any real solution's at this point. and i don't wanna crash it worse :(

---

### Post by mipstien on 2006-09-26
I am not sure if this is normal but every time i run fsck or e2fsck it says it changed the filesystem. didn't know if it always does that or if it is only when it is messed up.

---

### Post by mipstien on 2006-09-26
/dev/sda7: clean, 212534/13271040 files, 11698634/26515274 blocks

is what i get if i do not put -f on e2fsck

---

### Post by mipstien on 2006-09-26
ive run every logical command with e2fsck and it all outputs the same thing really, that it 'thinks' there are no error's
there is something wrong, i can't see any of my thumbnails for any of the files on the EXT3 file system but i can on all the NTFS file systems. i also can't hover over mp3's and play them but they play within an mp3 player. images show up when i click them but no thumbnails. those are just a couple of things i have seen. *confused*
ive done as much searching as i can, and i can't seem to find help anywhere PLEASE help.

---

### Post by mipstien on 2006-09-27
help PLEASE, im begging now!

---

