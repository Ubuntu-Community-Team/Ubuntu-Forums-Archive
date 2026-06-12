---
title: "To Partition or Not"
date: 2011-12-06
forum: Desktop Environments
---

### Post by Acharn on 2011-12-06
When I was first introduced to Un*x operating systems back in the '90s my mentor told me that because it was always possible for something to go horribly wrong with software it was a good idea to keep the user directories in a separate partition on the hard drive. That would make it easier, he claimed, to recover important user data if something destroyed the system. I'm wondering if there's any point to that nowadays. When my hard drive wouldn't boot Windows any more I accidentally erased the partition table while trying to rescue it, but then I was able to install Ubuntu 10.10 and have been running Ubuntu since (now upgraded to 11.10). I did partition my hard drive into two partitions, and put /usr/local in one and everything else in the other but I feel I'm wasting a lot of space this way. Almost all the "data" I want to keep is music or videos I download. My /usr/local partition is 76% full (31GB free), and the other partition is only 19% full (69GB free) and I don't expect to be installing much more software there.

I expect to be able to get a new, and probably larger, hard drive this month and was wondering what current best practice is. I've never done the homework I should have into the mechanics of the Un*x file systems, and I know there have been improvements since the early '90s. Is there any point to splitting my drive into more than one partition? Oh, yeah, and just as an aside, what would be the best size for my swap file partition? I guessed 3GB and it seems to work OK. Pointers to learning resources would be welcome, as would just plain "free advice, which is worth every penny you pay for it."

---

### Post by beew on 2011-12-06
There is a point to keep a seperate /home partition (/ and /home, not /usr/local) , it is for easy update of your OS. When time comes to update just do a clean install on the / partition (reformat the / partition, while NOT reformatting  /home, keep the labels as they are ) so you keep your data and settings (of course you may not want to keep all the settings so you can just delete the configuration files in question)  I don't do "upgrade" as the process is painfully slow and quite flaky. Of course this also applies if your system is toasted in such a way that would require reinstallation (again reinstall keeping the two partition layout, install into / ,--reformatting,--and keeping /home unchanged,--unreformatted)

---

### Post by Acharn on 2011-12-06
Ah. When I was working with our school's system I was using FreeBSD for my server. The file layout is a little different than Linux. IIRC on FreeBSD, at least up to 2006, the /home directory was under /usr/local, and there was a symlink in /. The root directory was also in /home. I see in Linux root is a separate directory in /. Interesting. I'm planning to use dd to transfer everything over to the new drive when I finally get it; guess I need to spend some time with the man page. At least I have a better idea of how much space the system needs, so next time I can do a better layout.

---

### Post by grahammechanical on 2011-12-06
+1 to beew's suggestion to have a separate / partiton for the OS and a /home partition for the rest. I have also found a fresh install to be better than an upgrade. Especially when going from 11.04 (and earlier), which was based upon Gnome 2, to 11.10, which is based on Gnome 3. 

Swap is usually about twice system RAM. Although if you have a lot of RAM you may never use swap. So, it may not need to be as large as 3GB. It also depends on whether you will use Suspend or Hibernation. There needs to be enough swap memory on the hard disk to hold the contents of system Memory (RAM).

Regards.

---

### Post by Paddy Landau on 2011-12-06
Ubuntu ideally has three partitions: root, /home and swap (in any order). They usually go into a logical partition because most people also have Windows and its recovery partitions on the drive. (The modern systems in development, however, will do away with logical partitions.)

> **grahammechanical said:**
> Swap is usually about twice system RAM.
That is no longer advised. The suggestion for twice RAM came from the days when RAM was horribly expensive, and swap extensively used. Nowadays, use the same amount of swap for RAM if you wish to hibernate, with a minimum of 1Gb swap if you have less than 1Gb RAM.

---

### Post by r_mano on 2011-12-06
I normally use two partitions (plus swap): / and /home --- so that I can reinstall a new system without touching my personal data. 

As soon as I finish installing, I arrange the system so that /usr/local is a symlink to /home/local (and the same for /opt, to /home/opt), so that when I compile my strange old programs from source they will stay there too after a reinstall.

---

### Post by mcduck on 2011-12-07
I'd definitely recommend using a separate partition to store user files, but you should still consider if you actually want that to be /home, or perhaps just some other location instead.

For example you will definitely want to get all your personal files back after a making a reinstall, but on the other hand you might not want all the configuration files from the previous install, especially not from a previous releaseor some other Linux distribution. Also you can't share a /home partition between different distributions or release versions.

What I usually do is keeping /home on root partition, but then creating a separate /storage partition for personal files, and then symlink various directories from /storage to user homes for easy access (for example /storage/mcduck/Music is linked into /home/mcduck/Music etc). When doing a release upgrade or something I just backup the rest of the stuff from home directories into /storage and afterwards pick which config fiels I actually want into the new system and which ones aren't needed. Bit more work to set up than just using a /home parttion, but much more flexibility...

---

### Post by Paddy Landau on 2011-12-07
There is one more consideration to take into account.

If you choose to encrypt your /home folder, then it is definitely easier to back up /home, reformat /home when reinstalling, and restore your data afterwards.

The process to restore access to an encrypted /home folder after reinstallation is hard to find, poorly documented -- incompletely so on the Ubuntu site -- and therefore hard to do successfully. Of course, if you want to go ahead anyway, be sure to save and print your 32-character passphrase beforehand. You can get it from the following command when logged in.```
ecryptfs-unwrap-passphrase
```

---

### Post by epsallidas on 2011-12-13
> **r_mano said:**
> As soon as I finish installing, I arrange the system so that /usr/local is a symlink to /home/local (and the same for /opt, to /home/opt), so that when I compile my strange old programs from source they will stay there too after a reinstall.

How do i do that too? I have partitioned my 500GB internal hard drive, this way: 20GB mounted at /, 478GB mounted at /home and the rest 2GB swap. The thing now is that i'm trying to install MATLAB and other big sized programs using /usr/local as the default installation directory and there is not enough free space. I thought to install them in a different directory located at /home but i want to see if there is another way.

---

### Post by r_mano on 2011-12-13
> **epsallidas said:**
> How do i do that too? 

What I do is the following (well, this is simplified --- you can do that with pipes etc but I write here the "easy" way). All of this has to be done with root privilege, so... take care. 

1) save what you have in /usr/local: 

```
cd /usr; tar cvf /home/local.tar local/
```

2) this should have created a file /home/local.tar with all the /usr/local content. Now recreate it under /home: 

```
cd /home; tar xvpf local.tar 
```

3) now you should have a exact copy of /usr/local in /home/local. Notice the "p" in the "tar" arguments, it's important. 

4) shuffle things

```
cd /usr; mv local oldlocal; ln -s /home/local local

```

5) now it's done. If all is gone well, you can remove /usr/oldlocal and you have a symlink: 

```
(0)romano-asus:~% ls -l /usr/local
lrwxrwxrwx 1 root root 11 2010-05-28 15:59 /usr/local ->/home/local
```

Note that this works if you do not have a /home/local dir (it will happen next time when you reinstall), in that case you have to merge the new and old local dirs which could be more complex. 

You can do the same with /opt; if /usr/opt does not exist you simply nedd

```
mkdir /home/opt; cd /; ln -s /home/opt opt
```

---

### Post by epsallidas on 2011-12-13
Thank you very much for your help r_mano! :D

---

