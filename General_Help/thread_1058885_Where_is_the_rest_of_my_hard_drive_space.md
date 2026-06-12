---
title: "Where is the rest of my hard drive space"
date: 2009-02-03
forum: General Help
---

### Post by sumpm1 on 2009-02-03
Hey guys. I have a 20gb partition that Ubuntu is installed on. In Nautilus, even if I show hidden files, when I select all of the folders on that drive and check the properties, it shows that about 6gb are used, which should leave me with around 14gb left. But instead, I have 6gb free in Nautilus on that partition. I have emptied my trash, and checked Gparted, and Gparted also says that 14gb are used (rather than 6) and that there are only 6gb left.

I want to backup this partition, so I am trying to minimize the size. Where are these files that are taking up the rest of my space? I cannot find them in Disc usage analyzer either.

Thanks

---

### Post by redilyn on 2009-02-03
Try using the Disk Usage Analyzer

Applications -> Accessories -> Disk Usage Analyzer

Then scan file system and have a look for whats taking the space

---

### Post by sumpm1 on 2009-02-03
> **redilyn said:**
> Try using the Disk Usage Analyzer

Applications -> Accessories -> Disk Usage Analyzer

Then scan file system and have a look for whats taking the space

Hey appreciate the help, but as I stated in the first post, I have also looked in the Disc usage analyzer, it shows 6gb being used, but gparted shows 14 gb being used.

---

### Post by icanfly0307 on 2009-02-03
Post the output of "sudo fdisk -l". That should give you an accurate measure of your partition space.

---

### Post by timcredible on 2009-02-03
do you have another partition on the drive?  also, keep in mind that drive makers use "GB" loosely - when looking at drive space in a computer operating system, it uses the correct measurement of 1GB, which is 2^30 bits.  drive makers say 1GB = 1 billion bits, which is wrong, but they do that to make it sound like they are selling a larger drive than they really are, so you'll always see a little less than advertised (not as much as you're reporting though).

---

### Post by jerome1232 on 2009-02-03
My guess is there are files that you don't have permission to view, and those are taking up space (they won't be included in those estimates)

To get an accurate picture

```
df -h
sudo du -hx --max-depth=1 /
```

---

### Post by sumpm1 on 2009-02-04
> **jerome1232 said:**
> My guess is there are files that you don't have permission to view, and those are taking up space (they won't be included in those estimates)

To get an accurate picture

```
df -h
sudo du -hx --max-depth=1 /
```

Thanks for that. I still have alot to learn about Linux and Ubuntu. THis is the output of the command you gave me. It seems that Ubuntu is simply RESERVING this space, so it appears "used" to Nautilus, Gparted, and other programs. So it seems that the directories /tmpfs, /varrun, and varlock are reserved partition space for the use of Ubuntu. But they are not filled as you can see. This means that if I create a backup of my partition, then they will not be make the file larger.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G   13G  5.7G  68% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  1.3M  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile


```

---

### Post by sumpm1 on 2009-02-04
All right. So I went to make a backup using tar, and forgot to start the terminal in the / directory. And so a full size backup.tgz was created, and used up 3.5gb, but I could NOT FIND the created backup file!!! I forget how I even stumbled onto this folder, but the /root/.local/share/trash/files directory (which may be the normal trash folder, but I don't think so) had some undeleteable files in there, including 8 gigs of backups! So I found the files that were hogging up my hard drive. And Nautilus now says there is 12+gb free as it should!

---

