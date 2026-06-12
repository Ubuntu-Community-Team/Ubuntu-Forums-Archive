---
title: "How to move home directory"
date: 2008-01-19
forum: Desktop Environments
---

### Post by ddavidd on 2008-01-19
I am installing a new computer for my children.
14 GB Windows 2000 (last Windows without activation!) NTFS
30 GB Ubuntu ext 3
2  GB swap
32 GB FAT 32 for the data, accessible from both systems

I have this system working well on my laptop (XP/Suse), but would prefer to move the home directories to the data parrtition to encourage all data to be saved there.
Is it possible to move home directories to a FAT 32 partition?
How?
Thanks!

---

### Post by ddavidd on 2008-01-19
The problem sems to be that the user has to own the home directory.
I changed the home directory path, but there was an error, to do with permissions.
root owns the new directory.
I tried to sudo chown it, but this didn't work
Is it possible to  change owner of a directory on a FAT32 partition? 

Anyone any suggestions?
Thanks

---

### Post by Keith Hedger on 2008-01-19
I think that fat32 does not fully support permisions i know it doesn't support symlinks, you may not be able to use a fat32 partition as /home try formating it as ext3 (!!! SAVE YOUR DATA FIRST !!!)

---

### Post by smartboyathome on 2008-01-19
Try using [this guide]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by rosegarden78 on 2008-01-20
EDIT: I deleted this because staff says mounting is automatic in GG.

---

### Post by ddavidd on 2008-01-20
Thanks, Keith. Does that mean that is im impossible to locate home on a FAT32 partition?

Thankd smartboyathome.
The guide details formatting partition as ext3

Thanks rosegarden. 
 Unfortunately, copying the home directory brings an error message.

Am I right to assume that it is impossible to have a home directory on a FAT32 partition? This was the intention, the whole idea is to be able to access alltest2 files from Linux and Windows. 
Actualy, I tried out saving onto the FAT32 partition, it is very uncomfortable. To much to expect from the children. Savig a file is easy and comfortable as long as it's into home. 

Any workarounds?

---

### Post by jacksaff on 2008-01-20
You can install ext3 drivers for windows. Put your data on ext3. It's a vastly better file system than fat32 - it has journaling (which windows won't use but doesn't hurt), gets a LOT less fragmented, supports symlinks and unix-like file ownership, is free, has open drivers and so on... 
The only hassle is that windows will write crummy thumbnail files and the like to all directories in which it finds anything that it thinks is a graphic, and is too dumb to know how to make them hidden.

---

### Post by Ardrias on 2008-01-20
Well you could make a EXT3 partition for /home, but then make like a "save stuff here" directory inside it where you mount the FAT32 disk. Or you could make the partition for files to NTFS and use NTFS-3G to mount it in Linux.

Edit: For the above about the thumbnails, you can turn that off in Explorer. Cant remember the name in english, but there's an option to disable thumbnail caching and the like.

---

### Post by rosegarden78 on 2008-01-20
EDIT: I deleted this because who know what to do if it won't mount anyway.

---

### Post by rosegarden78 on 2008-01-20
EDIT: I deleted this because the Staff tells me all this mounting stuff should be handled automatically in gutsy ...

---

### Post by rosegarden78 on 2008-01-20
EDIT:I deleted this because I think it says what my last post does.

---

### Post by rosegarden78 on 2008-01-20
EDIT: I deleted this because I think I pressed the button twice.

---

### Post by ddavidd on 2008-01-20
As a newbie, I am really impressed how many of you have taken time to meke good suggestions. 
Thanks:

I opened nautilus as root (this requires not root password, but my password, under which I installed Ubuntu - is that right?) and tried:
- to chown the new home directory to me or to the relevant user
- to change the group to the new user
- to copy the Ubuntu /home directory to the FAT32 partition
- I also tried these attempts in the terminal with prefix sudo and gksudo

All these attempts produced errors.

I think the suggestion to change the data partition to ext3 and install ext3 drivers under Windows seems promising, will trythat next. I have generally been impressed with open source aps under windows, have got rid of ever more bloatware recently

---

### Post by rosegarden78 on 2008-01-20
EDIT: I deleted this because even I had to chown instead of using a GUI yesterday.

---

### Post by ddavidd on 2008-01-21
I don't know if anyone is still reading this thread, but all attempte end in disaster.

I followed the instructionshere:
[http://www.psychocats.net/ubuntu/mountwindows#fat32](http://www.psychocats.net/ubuntu/mountwindows#fat32)
and actually got as far as dismounting the FAT32 partition and remounting it with group users. Unfortunately, home seems to have to belong to the user, still no go.

Then I gave up atempts to move home to the Fat32 partition and reinstalled Ubuntu with /home on an ext2 partition, intending to access this from Windows. (ext2 seems to be less of a problem)

Three apps, which all claim to access ext2 partitions from Windows:
I installed "win2fs",
This did not work, it wanted to format the ext2 partition
I installed "ext2 IFS", it reported an error when I tried to access a file and when I started Ubuntu, it did a disc check, which fortunately repaired the damage
I installed "ext2fsd", also didn't work.
Very fortunately, all these deinstalled without apparent damage.

So all attempts to unify the data have failed. 
Anyone got any suggestions?
I give up, have wasted three days work
Do any other Linux distributions permit home on a FAT32 partition?

---

### Post by Keith Hedger on 2008-01-22
I think you are stuffed if you want to put a home folder on a fat32 patition because as i said earlier fat32 dont support permissions or symlinks the best you can do i think is put the home partitions on ext3 and from windows ( i dont have windows install so im doing this from memory) move your "my documents" folder to your fat32 data partition and also the desktop folder etc ( is this possible ?) then make a symlink FROM the "my documents" folder on the fat32 partition TO the "Documents" folder in your home folders on the ext3 partitiion ie ```
ln -s "/PATH/TO/FAT32/My Documents" "/PATH/TO/HOME/USER/Documents"
``` and then the same for any other folders that widows allows you to move a lot of programs will save to "Documents" or "Desktop" by default, this way when you save to (for instance) Documents in ubuntu they will be available in "My Documents" from windows,
I know this isn't exactly what you want to do but I dont think theres any other way:(

---

### Post by rosegarden78 on 2008-01-26
It's just FAT32 won't support file permissions and symlinks.  I'm pretty sure Linux needs those things.  FAT32 makes a good format for data storage though just not running Linux.  It can run Windows though.  Forum Staff tells me to keep the /home and the / root file system on the same partition.  I follow their advice so I'm sorry I cannot offer any technical assistance good luck!

---

### Post by Keith Hedger on 2008-01-26
is there an echo in here? :):)

---

