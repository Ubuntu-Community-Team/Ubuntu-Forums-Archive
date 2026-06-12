---
title: "Low Disk Space Warning, A bug? Or a limitation?"
date: 2010-02-18
forum: Desktop Environments
---

### Post by 2hot6ft2 on 2010-02-18
I decide to give bleachbit a try today. Now I use other tools to keep my file system clean anyway but while running it there was a warning popup stating:
**This computer has only 1.3GB disk space remaining.**
I didn't take a screenshot of that one but I did the next time. I clicked on the Examine button and like I thought I had **29GB of free disk space**.
Pic below.

Ran bleachbit again this time as root and it poped up again. This time stating that:
**This computer has only 642.8MB disk space remaining.**
Pic below.
I clicked on Examine again this time it showed that I have **29.7GB of free space**.
Pic below.

Now in the Disk Usage Alalyzer results it shows that:
**/ is 100% used**
**/user is 85.2% used**
and on the second run
**/user is 80.5% used**

So if I have 29GB of free space on the partition my questions are these:
1. Is there a limit to the file system size short of the size of the partition?
2. Is it limited by the number of files in the file system?
3. Is it limited by the combined size of the files in the file system?
4. If 3 is true then what exactly is the limitation in MB/GB?
5. Is there a way to increase the capacity of / OR /usr?
6. Is this a bug?
7. Is there need for concern?
8. If this is not a bug, a limitation, or a need for concern, then why does it show the warning at all?

Thanks for taking the time to clarify this.

---

### Post by oldos2er on 2010-02-18
It looks like you have a 10GB root partition, is that correct? If you want to increase its size, you'll need to boot from the Ubuntu LiveCD and run gparted from there.

Could you run **sudo fdisk -l** in a terminal, and post the output here?

---

### Post by mcduck on 2010-02-18
> **2hot6ft2 said:**
> I decide to give bleachbit a try today. Now I use other tools to keep my file system clean anyway but while running it there was a warning popup stating:
**This computer has only 1.3GB disk space remaining.**
I didn't take a screenshot of that one but I did the next time. I clicked on the Examine button and like I thought I had **29GB of free disk space**.
Pic below.

Ran bleachbit again this time as root and it poped up again. This time stating that:
**This computer has only 642.8MB disk space remaining.**
Pic below.
I clicked on Examine again this time it showed that I have **29.7GB of free space**.
Pic below.

Now in the Disk Usage Alalyzer results it shows that:
**/ is 100% used**
**/user is 85.2% used**
and on the second run
**/user is 80.5% used**

So if I have 29GB of free space on the partition my questions are these:
1. Is there a limit to the file system size short of the size of the partition?
2. Is it limited by the number of files in the file system?
3. Is it limited by the combined size of the files in the file system?
4. If 3 is true then what exactly is the limitation in MB/GB?
5. Is there a way to increase the capacity of / OR /usr?
6. Is this a bug?
7. Is there need for concern?
8. If this is not a bug, a limitation, or a need for concern, then why does it show the warning at all?

Thanks for taking the time to clarify this.
You are misreading the information from the Disk USage Analyzer.

It's actually telling you that you are analyzing the root partition, (so the amount of used space on / is 100% of the amount of used space on root). Not that the / would be 100% full. Then, it's telling you that from the amount of data on your root partition 85,2% is in /usr, 10,5% is in /var, 4,9% in /home and so on..

So, the percentages you see are not telling you how full or empty different places are, they are telling you how large percentage of the data is in that place. (If you abnalyzed, say, /home instead of /, then the DUA would show /Home as 100%, and then siaply have large portion of the data inside /home is in each subdirectory. So the directory you ananlyze is always 100% and other directories dispaly the percentage of the total analyzed data contained in them).

If you have /usr on the same partiton as the /, then you have exactly the same amount of available space on /usr as you have available space on the partition itself. There is no per-directory size limits (unless you enable quotas and set suych limits yourself).

If you want to get a simple, easy overview of available and used space on your partitions open a terminal and run "df -h". Post the output here if you need somebody to explain it in detail.

edit: I see nothing there that would indicate that your partitioons would be full. If Bleachbit claims so then it must be a bug in Bleachbit. But use the "df -h" to confirm the amount of used/free space.

---

### Post by 2hot6ft2 on 2010-02-18
> **oldos2er said:**
> It looks like you have a 10GB root partition, is that correct? If you want to increase its size, you'll need to boot from the Ubuntu LiveCD and run gparted from there.

Could you run **sudo fdisk -l** in a terminal, and post the output here?
No, I have Ubuntu install on a 40GB partition it's not a separate partition
Here's  the results of sudo fdisk -l in a terminal
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd03d783

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       60801   452543017+   5  Extended
/dev/sda5            9741       59236   397576588+   7  HPFS/NTFS
/dev/sda6           60553       60801     2000061   82  Linux swap / Solaris
/dev/sda7           59237       60552    10570738+  83  Linux
/dev/sda8            4463        9740    42395472   83  Linux

```
From the installed system
and how it looks in gParted sda8 is ubuntu the other one sda7 is BackTrack
sda5 is encrypted that's why it shows the caution icon so it's not a problem.

---

### Post by 2hot6ft2 on 2010-02-18
> **mcduck said:**
> You are misreading the information from the Disk USage Analyzer.

It's actually telling you that you are analyzing the root partition, (so the amount of used space on / is 100% of the amount of used space on root). Not that the / would be 100% full. Then, it's telling you that from the amount of data on your root partition 85,2% is in /usr, 10,5% is in /var, 4,9% in /home and so on..

So, the percentages you see are not telling you how full or empty different places are, they are telling you how large percentage of the data is in that place. (If you abnalyzed, say, /home instead of /, then the DUA would show /Home as 100%, and then siaply have large portion of the data inside /home is in each subdirectory. So the directory you ananlyze is always 100% and other directories dispaly the percentage of the total analyzed data contained in them).

If you have /usr on the same partiton as the /, then you have exactly the same amount of available space on /usr as you have available space on the partition itself. There is no per-directory size limits (unless you enable quotas and set suych limits yourself).

If you want to get a simple, easy overview of available and used space on your partitions open a terminal and run "df -h". Post the output here if you need somebody to explain it in detail.
Ok, I see what you're saying, I think. It's not looking at the partition just the file system itself and how the data is spread out within the file system.
No I have not set any limits (quotas) myself.

Results of df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              40G  9.9G   28G  27% /
udev                  1.4G  328K  1.4G   1% /dev
none                  1.4G  420K  1.4G   1% /dev/shm
none                  1.4G  208K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw


```

---

### Post by 2hot6ft2 on 2010-02-18
So in this it's more representative of the actual use of the partitions space.
```
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda8              40G  9.9G   28G  27% /[/COLOR]**
udev                  1.4G  328K  1.4G   1% /dev
none                  1.4G  420K  1.4G   1% /dev/shm
none                  1.4G  208K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw

```
Meaning that roughly 27% of the partition is being used by the file system.

---

### Post by 2hot6ft2 on 2010-02-18
That would answer questions 1-5 and 7 leaving only 6 & 8
6. Is it a bug that it notifies you that you're out of disk space when you're not?
And
8. If this is not a bug, a limitation, or a need for concern, then why does it show the warning at all?

I have seen several threads on the warning and until now I thought maybe they had actually filled their partitions up with stuff.
That not being the case why does it give the warning?
It certainly does create un-necessary concerns.
If it's not actually reporting the partitions free space, can the warning be safely disabled?

---

### Post by mcduck on 2010-02-18
> **2hot6ft2 said:**
> So in this it's more representative of the actual use of the partitions space.

Meaning that roughly 27% of the partition is being used by the file system.

Yes, df tells you the amount of used & available space of partitions. Disk Usage Ananlyzer tells you how much of the total data is in each subdirectory of the directory you analyzed.

Your root is a 40GB partition, from which 9,9GB is used. 

So you sure are not running out of free space unlike what the Bleachbit is claiming. I must say that Bleachbit doesn't really seem like the kind of program I'd trust to do anyhting on my computers, at least based on the amount of problems people are having with it. Seems way too buggy a this point.  Besides, most of the stuff it removes can either be removed with the responsible program itself (firefox, apt) or shouldn't usually even be removed at all and contributes very little to the amount of used space on your system.. :)

---

### Post by 2hot6ft2 on 2010-02-18
> **mcduck said:**
> Yes, df tells you the amount of used & available space of partitions. Disk Usage Ananlyzer tells you how much of the total data is in each subdirectory of the directory you analyzed.

Your root is a 40GB partition, from which 9,9GB is used. 

So you sure are not running out of free space unlike what the Bleachbit is claiming. I must say that Bleachbit doesn't really seem like the kind of program I'd trust to do anyhting on my computers, at least based on the amount of problems people are having with it. :)
It was apparently triggered when I ran bleachbit but I don't think everyone that received the same warning was using it. I'll search thru the previous threads about the warning and see if they mention using it. I have to agree I wont be using it again if there are problems with it as it's a pretty powerful tool that can be run as root.

---

### Post by 2hot6ft2 on 2010-02-18
I'll consider this as solved and not use bleachbit. I see in another thread how to manage the warning configuration which I'll quote here for others:
> **SecretCode said:**
> While trying to solve this for myself I came across your post. And this is the solution:

Open **gconf-editor** (type gconf-editor at the command line), and navigate to the key **/apps/gnome_settings_daemon/plugins/housekeeping/**.

Double-click the **ignore paths** name, and remove the paths you want not to ignore any more.

There are some other useful configuration settings here, like free_percent_notify (default 0.05 meaning notify when space is less than 5%) and free_size_gb_no_notify (default 2 meaning don't notify if the free space is more than 2GB).

Thanks for the help mcduck and oldos2er

---

### Post by firekage on 2012-12-21
I would like to add that this bug is still present in 12.10 and with dconf-editor it could be not fixed because there is no key /apps/gnome_settings_deamon/plugins/housekeeping.

We have to move two files to a different place, these files are: 

> housekeeping.gnome-settings-plugin 
libhousekeeping.so

---

### Post by overdrank on 2012-12-21
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

