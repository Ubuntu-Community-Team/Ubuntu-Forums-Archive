---
title: "Sharing a home folder with windows?"
date: 2009-04-19
forum: General Help
---

### Post by Dvorakis on 2009-04-19
Is sharing a home folder between ubuntu and windows a possibility?

I basically have one hard drive that is for ubuntu(its about 150GB or so) that I use for everything thats not video games.  It has all my music on it, but I have and Ipod touch, and I can't sync it so I have to use a windows partition to sync it.

Usually this is fine,seeing as I use two hard drives and one is always a windows partition...but the problem is I don't have the space on the windows drive to keep my music anymore(Its only about 40 gigs,and very old). Does anyone know a way that I can either share the home folder(for music) from my ubuntu hard drive to my windows HD.  Or If I install a new partition on my ubuntu hard drive(just big enough for windows so I don't lose space) that I could share the music between those.

All this time I want to not transfer music from partitions, I simply want to be able to constantly access it from my ubuntu home folder.

If you need more info,ask me.
THANKS! Dvorak.

---

### Post by Vaphell on 2009-04-19
you can try this
[http://www.fs-driver.org/](http://www.fs-driver.org/)
it allows you to use ext2 partitions in windows
ext3 ones also work (backward compatibility), but with no journaling

it worked for me just fine

---

### Post by lovinglinux on 2009-04-19
You can create a new partition on Ubuntu as NTFS and mount it under a home directory, like for example /home/Dvorakis/sharedmusic. There is no need to share the entire home.

When using Ubuntu, you will be able to see the partition as a directory. When using Windows, it will see the partition with music as a single drive.

---

### Post by Dvorakis on 2009-04-19
Awsome! Will I have to install a windows partition on the ubuntu hard drive or will two hard drives still work?

And can anyone give me a guide...things ussually go better with a guide.

Again. Thanks a MILLION.

EDIT: Also, is there an option to create an expandable partition?Where is takes up as much space as it needs and expands as I add to it?

---

### Post by lovinglinux on 2009-04-19
> **Dvorakis said:**
> Awsome! Will I have to install a windows partition on the ubuntu hard drive or will two hard drives still work?

I don't understand your question. Do you want to install Windows on a new partition or do you want a new partition for media files? These are very different procedures.

As far as I understand, you have Windows installed on a hard drive and Ubuntu on another. Since your Windows disk has low capacity, I would leave Windows untouched and create a new partition on the Ubuntu hard drive, formatting it as NTFS and mounting it under /home/Dvorakis/whatever. You might need to shrink you current partition to make space for the new one. This new partition will not contain any OS, just media files. Since it will be NTFS, Windows will be able to see it, so you can use it to save your media from Windows and read/edit them on Ubuntu.

A partition acts like an additional drive. It doesn't matter where the partition is located, as long you format it with the correct file system. If the partition will be used only by Ubuntu, then you can format it as ext3. If the partition will be used by Ubuntu and Windows, then you should format it as NTFS, because Windows cannot read ext3 but Ubuntu can read NTFS.

> **Dvorakis said:**
> And can anyone give me a guide...things ussually go better with a guide.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

> **Dvorakis said:**
> EDIT: Also, is there an option to create an expandable partition?Where is takes up as much space as it needs and expands as I add to it?

I'm afraid not. You can see on the tutorial above that it has an extended partition, but it doesn't mean it will grow when needed. Extended partitions are like a single partition containing sub-partitions. The sub -partitions act like any other partition, but they are sometimes necessary if you have already reached the limit of 4 primary partitions.

---

### Post by Dvorakis on 2009-04-19
Sorry for confusing you. I understand completely now,and that sounds perfect. I'll try to get it done and tell you when I complete it or If I get problems.

Thanks again!This is exactly what I needed.

---

### Post by lovinglinux on 2009-04-19
> **Dvorakis said:**
> Sorry for confusing you. I understand completely now,and that sounds perfect. I'll try to get it done and tell you when I complete it or If I get problems.

Thanks again!This is exactly what I needed.

Good luck. Once you understand the concepts of partitions and mounting points it will be pretty easy.

I have for example an additional hard drive that I have mounted under */home/lovinglinux/media*. So when I browse it, it looks like a simple folder called "media" under my home directory, but it is actually a separate hard drive dedicated to store media files only. I also have a separate partition in the main hard drive for the /home directory. So all my home folders and files are stored on a separate partition on the main hard drive, but /home/lovinglinux/media files and sub folders are stored on another disk. Weird isn't it?

What is weird for someone used to Windows is that mounting points gives you a lot of flexibility on how to store and organize data using separate partitions and hard drives, but still browse them as they were part of the same directory structure. Windows can't give you that, since it consider each partition as a new drive and automatically assign letters to them.

---

### Post by paradigm2 on 2009-04-19
> **Dvorakis said:**
> Is sharing a home folder between ubuntu and windows a possibility?

I basically have one hard drive that is for ubuntu(its about 150GB or so) that I use for everything thats not video games.  It has all my music on it, but I have and Ipod touch, and I can't sync it so I have to use a windows partition to sync it.

Usually this is fine,seeing as I use two hard drives and one is always a windows partition...but the problem is I don't have the space on the windows drive to keep my music anymore(Its only about 40 gigs,and very old). Does anyone know a way that I can either share the home folder(for music) from my ubuntu hard drive to my windows HD.  Or If I install a new partition on my ubuntu hard drive(just big enough for windows so I don't lose space) that I could share the music between those.

All this time I want to not transfer music from partitions, I simply want to be able to constantly access it from my ubuntu home folder.

If you need more info,ask me.
THANKS! Dvorak.

Yes it is fairly easy to do.

Install the samba package and then modify the config file, I believe /smb.conf

There are just a few lines that you will need to uncomment in order to do this (it is fairly easy).

You will also likely have to add the user using the samba utility, I believe smbpasswd (not sure off the top of my head).  You then access it from windows using this user name and password.  If the username and passwd is the same on both ubuntu and windows, it should even work automatically.

I now use sshfs so my info is hazy, I apologise.  But it should give you a bit of info until someone else helps further.  And it is definitely possible.

See this doc for general info on samba:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

They do have graphical utilities to help configure it, but I just found manually changing the config file to be easier.

---

