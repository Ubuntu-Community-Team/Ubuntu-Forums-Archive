---
title: "Cannot open &quot;Computer&quot;"
date: 2010-01-30
forum: Desktop Environments
---

### Post by Abhijit Navale on 2010-01-30
I am unable to open 'Computer'.
It is located in Places => Computer.
When this happens I cannot right click on the desktop. 
But I can open other places such as Home, Documents.
And when I try to rename the microsd card then the rename option is disabled.
Though the "Computer" accidently opens then there is nothing inside it i.e. no icons etc.
Also if I try to open it by clicking, then other places which are already opened automatically gets closed e.g. Documents etc.
The first time this happend when I conneced Kingston microsd card reader.
I am using Ubuntu for more than 2 months But i dont get this error before.
I started to get this error after installing various themes, windows borders, icons etc. using software called 'Art Manager'

I reported this bug here : [https://bugs.launchpad.net/ubuntu/+bug/375713](https://bugs.launchpad.net/ubuntu/+bug/375713). Thanx to 'bitplane' on #ubuntu irc for pointing out me at this link.

Is is VIRUS?
OR
Is this just mulfunctioning?
Please guide me to solve this.

---

### Post by gdonwallace on 2010-01-30
It almost sounds like a permissions problem, although that would be weird.

Try this.  Open a terminal and type: **gksudo nautilus** and see if that makes any difference for you.  Also you might want to check the preferences to make sure that show hidden and backup files has a check mark in front of it.  I can't see that not allowing anything to show up; but its worth having it checked just in case.

---

### Post by Abhijit Navale on 2010-01-30
when i run gksudo nautilus it asked me root password and then i get root file browser and i terminal i got these erros:
administrator@abhi-laptop:~$ gksudo nautilus

--- Hash table keys for warning below:
--> file:///root

(nautilus:13347): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(nautilus:13347): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

---

### Post by gdonwallace on 2010-02-01
When was the last time that your system ran a file system check (FSCK).  It seems that it is having problems reading your root drive.  

I would suggest running the fsck utility.  On boot up, press enter when it comes to the GRUB countdown.  Choose the option to go to root without networking.  type fsck and let it run.

---

### Post by Abhijit Navale on 2010-02-05
When tryied to run fsck, it says
cannot check mounted drive!
First unmount sda1

---

### Post by MooPi on 2010-02-05
To run fsck or e2fsck, you will need to boot from your live CD and open a terminal ```
e2fsck -n
```You may have to use ```
sudo e2fsck -n
```

---

### Post by Abhijit Navale on 2010-02-05
Ok I wll do that.

One supplemetary question.
After enabling some extra effects in compiz settings such as desktop cube, rotate cube, blur windows, ring switcher etc etc all these operations get slow on performance.
Is this because of my slow graphics card or what can the reason be?

---

### Post by Abhijit Navale on 2010-02-07
When try to run command e2fsck if got this:

ubuntu@ubuntu:~$ e2fsck -n
Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ fsck -n
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ e2fsck -n
Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ sudo e2fsck -n
Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ sudo e2fsck -n sda1
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: No such file or directory while trying to open sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -n sda
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: No such file or directory while trying to open sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by Abhijit Navale on 2010-02-14
anyone?

---

### Post by duke.tim on 2010-06-15
I had a similar problem and the fix that sorta worked for me was located here
[http://www.linuxforums.org/forum/ubuntu-help/141637-solved-nautilus-cannot-handle-computer-locations.html](http://www.linuxforums.org/forum/ubuntu-help/141637-solved-nautilus-cannot-handle-computer-locations.html)

okay how it worked was simple (hope you're still getting on the fourms)

```
sudo mv /usr/local usr/local.old
sudo mkdir /usr/local
```
you might need to transfer some of your files if you installed programs that put stuff in them like logger pro

---

### Post by doas777 on 2010-06-15
well, one thing at a time
1) for nautilus:
open a terminal (Applications -> Accessories )
and run```
nautilus
```once nautilus is open, hit Ctrl + L and in the location bar, paste in:
```
computer:///
``` and hit enter

does it come up, and/or does it print an error message in the terminal?

2) SDCard
Renaming a volume is a system level activity so you need to be running whatever app changes it with sudo or gksu. try going to System -> Administration -> Disk Utility and see if you can rename it from there. if you use it on the liveCD, you can also use it to perform a fsck.


3) to run fsck, the syntax is 
```
sudo e2fsck /dev/sdXX
``` not just 'sda1' 

4) yes compiz will really slow down a system with a weak vid card or other attribute (CPU, System Bus, RAM speed/amount, etc).

---

