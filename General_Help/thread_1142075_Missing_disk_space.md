---
title: "Missing disk space?"
date: 2009-04-28
forum: General Help
---

### Post by pentium_3 on 2009-04-28
A while ago I replaced Windows XP with Xubuntu on my brother's aging computer. We had a few minor glitches, but overall I was very happy with the increase in performance. Now we have another problem...

Now, I'm not sure if this is just me, or if it is a known issue, or what. The computer has a somewhat new 80 GB hard drive, which is reported as 79 GB in Xubuntu. OK, so far so good. The computer reports 56.2 GB of free space. Now here is where the problem is. The file system reports 14.7 GB of space used. However, if this is correct, then there should be 64.3 GB of free space left, NOT 56.2

Where is the other 8.1 GB? Why is the computer reporting so much less? Are there temporary files that need to be deleted? Any help on this would be greatly appreciated.

---

### Post by 3Miro on 2009-04-28
There was a tread somewhere about some percentage of the HD being reserved so that the system can operate even if the HD gets full.

Have you accounted for swap and how much of a swap partition do you have.

What are you using to read the HD. Go to the Xfe terminal and type:
```
df
```

That will list partitions and their usage.

---

### Post by drs305 on 2009-04-28
By default 5% of the space is reserved for system use. You can change it if you feel you must with the tune2fs command (see the man page).

For finding "lost" space in general, I've written a fairly lengthy HOWTO. The link is in my signature line. It includes the tune2fs command instructions if you feel you need to change it.

Added: By the way, welcome to the ubuntu forums.

---

### Post by pentium_3 on 2009-04-28
Hi, 

Thanks for the responses. The swap partition on this computer is pretty miniscule, only about 635 MB. I went into the terminal and did the df thing and this is what I got:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76886272  14036732  58974664  20% /
varrun                  111604       100    111504   1% /var/run
varlock                 111604         0    111604   0% /var/lock
udev                    111604        44    111560   1% /dev
devshm                  111604         0    111604   0% /dev/shm
lrm                     111604     39792     71812  36% /lib/modules/2.6.24-23-generic/volatile

There are a bunch of little partitions all over the place. I can find my way around Windows and Mac OS 8 very easily, but I cannot for the life of me figure out what all these are supposed to be. Any ideas?

btw, drs205, thank-you for the welcome message. Much appreciated. :)

---

### Post by drs305 on 2009-04-29
> **pentium_3 said:**
> There are a bunch of little partitions all over the place. I can find my way around Windows and Mac OS 8 very easily, but I cannot for the life of me figure out what all these are supposed to be. Any ideas?

If by "little partitions" you mean the ones shown as a result of the "df" command, such as *varlock*, don't worry about them. They are just reported by the system but are not physical partitions. The actual partitions on your drive are the ones beginning with "/dev/". As an example, here is what part of mine looks like:
> 
me@mycomputer:~/Desktop$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
**/dev/sda10**    ext4     10G  3.2G  6.3G  35% /
tmpfs        tmpfs    2.0G     0  2.0G   0% /lib/init/rw
varrun       tmpfs    2.0G  356K  2.0G   1% /var/run
varlock      tmpfs    2.0G     0  2.0G   0% /var/lock
udev         tmpfs    2.0G  192K  2.0G   1% /dev
tmpfs        tmpfs    2.0G  676K  2.0G   1% /dev/shm
lrm          tmpfs    2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-generic/volatile
**/dev/sda3**     ext4     50G  9.6G   38G  21% /media/av
**/dev/sdb1**     ext4     48G   36G   11G  78% /media/backup
**/dev/sda2**     ext4     15G  3.0G   11G  22% /media/data

You can see from this partitial list that I have the same system "stuff", that the OS I am currently running is on is "/" on  /dev/sda10, and that I have 3 other partitions existing on two separate drives (sda, sdb).

Note you can add a switch to the "df" command to make it more readable: *df -Th* produces the following format (one line shown for the example):
> Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda10    ext4     10G  3.2G  6.3G  35% /


Ok, back to the question at hand. I was actually surprised to see that an 80GB disk reported having 79GB capacity. I don't know how that result was obtained but after formatting the manufacturer's reported capacities rarely match the actual available disk space. There have been various threads on that topic and artilces posted on the internet about drive capacities. [_This link_]("http://www.hardwaresecrets.com/article/482") indicates you would normally lose about +-6GB per 80GB drive for formatting, which gets close to your numbers. 

The link to "lost disk space" in my signature covers a lot of the reasons why reported and actual space vary. 

You specifically mentioned possible temporary files. I also wrote a tutorial about finding and deleting trash folders (link also in my signature line) and you can search for and delete those files according to the instructions in that link. If you have deleted files, especially as 'root', and haven't taken specific steps to empty root's trash bin, it could explain some of the discrepancies. For a quick look at root's trash, see if any files are reported with "*sudo ls -la /root/.local/share/Trash/files*". If found, the instructions on how to delete them are in the Trash guide referenced below.

Additionally, the various commands and applications used to report disk usage vary at what they look at, and some don't report space taken up by files you don't own. If you run commands such as "df" and "du" or gui apps such as Baobab/Disk Usage Analyzer as root (sudo/gksudo) you will often get different results than if you ran them as a normal user.

If the discrepancy still bothers you, run through the "lost disk space" guide step by step to ensure your system doesn't have files on it you don't know about and don't want. Then sit back and enjoy Xubuntu.

---

### Post by pentium_3 on 2009-04-29
> **drs305 said:**
> 
If the discrepancy still bothers you, run through the "lost disk space" guide step by step to ensure your system doesn't have files on it you don't know about and don't want. Then sit back and enjoy Xubuntu.

Thanks very much for all the help. I will run those tests immediately- and thanks for the info about the hard disk formatting process, as I found that rather odd too- on my ThinkPad T400, which is formatted with NTFS, a 160 GB drive is actually only 149 GB- so I was somewhat curious to see an 80 GB drive being reported as 79 Gigs. 

Bit by bit, I'm beginning to figure out this operating system...

---

