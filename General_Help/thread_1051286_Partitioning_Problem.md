---
title: "Partitioning Problem"
date: 2009-01-26
forum: General Help
---

### Post by StateofMind on 2009-01-26
I'm trying to get Ubuntu installed onto my desktop to dual boot with XP. I've looked at guides on how to do this, but I'm running into an error at the partition screen.

First I chose the first guided option, that installs Ubuntu alongside Windows itself. I got an error while it was resizing.

Now I'm trying to do it manually, and I'm still getting an error when I try to resize my Windows partition.

"An error occurred while writing the changes to the storage devices.

The resize operation has been aborted."

This happens just about as soon as it starts working.

Also worth noting; a couple of times it loaded without the first "guided" option available. Also, on manual it didn't show a value for the "used" size and I had no way to change it.

---

### Post by taurus on 2009-01-26
To make life a little easier, boot into windows and defrag your harddrive a couple of times.  Then, see if you can resize your harddrive with gparted from Ubuntu LiveCD now.

---

### Post by StateofMind on 2009-01-26
I've already defragged in Windows. I ran GParted and also got an error when trying to resize.

Another note: From what I've read, Windows should be on the /1 partition? Mine is on /2.

---

### Post by taurus on 2009-01-26
Post the output of this command from a terminal from the LiveCD.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by StateofMind on 2009-01-26
> **taurus said:**
> Post the output of this command from a terminal from the LiveCD.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

Usage: fdisk [-b SSZ] [-u] DISK Change partition table
fdisk -l [-b SSZ] [-u] DISK List partition table(s)
fdisk -s PARTITION Give partition size(s) in blocks
fdisk -v Give fdisk version

I google'd my problem and found someone who had a similar situation. They fixed it by "turning off static pagefile." I don't know what that means though...

Leaving for work.

---

### Post by StateofMind on 2009-01-26
Still haven't been able to get this to work.

I looked at the details of the problem partition in GParted, and apparently the problem has something to do with "clusters." Missing clusters, extra clusters, etc... Actually, here:

[IMG]http://i41.tinypic.com/35mqhd3.png[/IMG]

Really wanting to get this installed, can anyone help?

---

### Post by StateofMind on 2009-01-27
I ran /chkdsk /f (took forever!) and then defragmented again. It seemed to help, I guess. The installer was able to *try* to resize the partition for a lot longer. Stayed at 0%, working for about 10 minutes probably. Still nothing though.

---

### Post by StateofMind on 2009-01-27
One last bump. Anyone?

---

