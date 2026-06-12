---
title: "please help =(   must be superuser to use mount"
date: 2006-09-20
forum: Desktop Environments
---

### Post by samssf on 2006-09-20
Ok, after having huge problems with 64bit ubuntu on AMD64, I decided to wipe and start over using 32bit ubuntu.

When I was running 64bit, I had the pmount problem upon install but was quickly resolved...

This time forever, I have a new problem, and I am exteremly frustrated. I need to get my system up and running, but my wireless card wont work, I cant read from my partitions, etc... I have read every howto and done everything I can possibly think of, and yet no one out there has any decent answer for any of my problems.

My first major thing with this new install, is that when I would try to access "53 Gig volume" in "Computer", I would recieve the error "Mount: root cannot mount /dev/sdc1 on /media/sdc1" or something like that.

The suggestion was given to chmod 777 /mount/bin so I did. Makes no sense why I would have to do that, but ok.

Now when I try to access the partition from Computer, I receive this error:
"mount: must be superuser to use mount"

Really, this is a bunch of bs. There should be some info somewhere online on how to fix this. Surely, if I just finished my install, then other people would have the same problem upon install.

I have tried tweaking my fstab. Everone tells how to modify the CDROM entry. I need to know how to edit an entry for an ntfs partion.
Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sdc2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sdb1 /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sdc1 /media/sdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sdc5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0

Someone PLEASE help me or direct me to where I can find my solution.

---

### Post by kidders on 2006-09-20
Hi there,

Doing a **chmod 777** won't change the fact that you're not root, but it will allow viruses/malicious users to modify your "mount" command to do things it shouldn't. Undo that!! In any case, requiring root privileges to perform mount operations is pretty essential to security ... it's not some sort of problem.

/etc/fstab entries executed during boot are run as root, so there's no problem there. You need something along the lines of:

```

/dev/sdc1 /mnt/windows ntfs ro,noexec,auto 0 0

```

If you really wanted to, you *could* add "user" or "users" to the mount options for the partition, to allow ordinary users to mount/dismount the filesystem. Since you'd need to be root to make the change, it's at least relatively safe.

Hope that helps!

---

### Post by samssf on 2006-09-20
Err, no. I haven't heard of anyone having issues mounting partitions right upon boot (except for a couple things which are mentioned in the ubunto startup guide). I installed the 64 bit version of ubuntu 5 days ago and had no problems whatsoever mounting my ntfs partitions.

And so, I have an update... although I'm not real sure what's going on.. I will tell what I Know.

Mounting was giving me lots of errors on my sdc1 partition (windows xp ntfs). I tried lots of things (which never worked for anyone on any other forums), and likewise came up with nothing. Then I found a automatic mount script when helped me by giving me an error about block size and unknown filesystem type or some crap like that.

So I decided to try to boot to windows, and grub gives me an error that says "Filesystem type unknown. partition type 0x7"

Turns out a lot of people online got this error, and a lot of them when they dual boot. Unfortunately, I read for hours and never found a post where someone actually had their problem solved. Everything just asks whether or not the grub config is set up right.

Well, my grub config is correct. I know how to use the command line to try to boot to a partition. And I've tried setting my HDD to LBA. None of this helped. The problem won't be solved by changing Grub config or mappings and whatnot.

I am not too knowledgable when it comes to partitions and MBR.... but I think ubuntu (for some reason only with my latest install).. Installed grub onto my windows partition. Is that possible? Rather than installing it into the MBR. If I overwrite my MBR with a different tool... and tell that tool to boot to windows partition... then GRUB still comes up at that point. And from there, if I choose windows, it wont load (partition type 0x7)... and if I choose linux, Ubuntu loads (but without access to that windows ntfs partition)

Maybe the reason linux cannot recognize my windows partition filesystem is because if f'ed it up with grub?? I'm not sure...

I need to know what tools, if any, will allow me to

1. fix my mbr
2. get rid of grub from my windows partition
3. fix my windows partition.

I am sure something is f'ed up thats why I cant mount that partition from within ubuntu. OH and if I load gparted... it has an exclamation mark by my windows NTFS partition.

been nothing but hell since i installed ubunutu.... lost like 50 hours of time, and it's crazy because no one has any information about any of my problems. and yet, I've followed all instructions exactly.


Device Boot Start End Blocks Id System
/dev/sdc1 * 1 7014 56339923+ 7 HPFS/NTFS
/dev/sdc2 7015 8959 15623212+ 83 Linux
/dev/sdc3 8960 9039 642600 5 Extended
/dev/sdc5 8960 9039 642568+ 82 Linux swap / Solaris

---

### Post by kidders on 2006-09-20
> Mounting was giving me lots of errors on my sdc1 partition (windows xp ntfs). I tried lots of things (which never worked for anyone on any other forums), and likewise came up with nothing. Then I found a automatic mount script when helped me by giving me an error about block size and unknown filesystem type or some crap like that.

Hmm... seeing some of these messages would have been handy. Quite often, the specifics of exactly what you did, and what the system said to you are very helpful.

I really hope we can find what you did wrong! I suppose the first thing to do is take a look at your grub configuration, although I suspect your NTFS partition has been corrupted somehow :-( Did you try to write to it with Linux, by any chance?

With regard to your grub questions, it is possible to "install" grub into a partition, rather than a disk's MBR, but you'd have to have specifically asked it to do that. It's not something I've ever tried, so I have no idea how recoverable the affected partition might be, I'm afraid.

Unfortunately, running into a problem nobody else is having is a *very* bad sign! Oh dear!

**Edit:** Are any of the utilities in ntfstools proving any help in diagnosing your problem?

---

### Post by samssf on 2006-09-20
Thanks for the reply.

Yeah, I'm pretty sure the NTFS partition is corrupted. I don't quite remember whether or not I instructed GRUB to be installed onto something other than the default location when I installed linux, but I'm guessing I did.

That would be the only thing I could have done wrong. All other things I tried I was extrely careful on, and are commands or actions that I've performed before without any problems. 

The "Filesystem type unknown partition type 0x7" error is something that I will get any time linux tries to access my NTFS partition. (During boot, while trying to mount, etc)

I did not change anything after installing, and this SHOULD work immediately after install... so it must have been something with the installation.


I am not familiar with NTFSTools - I need to go to work but I will look this up later on and see what I can find. 

Thanks for the info

---

### Post by kidders on 2006-09-20
Hmmm :-( It'd be really unfortunate if the filesystem turned out to be unrecoverable. Linux provides a basic toolset for each filesystem it supports, which is the reason I mentioned the NTFS set (called ntfstools). It's maybe a bit of a long-shot, but it has to be at least worth trying.

Most filesystems are pretty reliant on the stuff they keep at the top end of a partition, so if grub *did* find its way onto, say, /dev/sda1 rather than /dev/sda, I'm afraid I don't know enough to help you reconstruct the overwritten bits. It's not encouraging that it used to work okay and suddenly stopped :-(

Perhaps Windows-based NTFS filesystem repair utilities will be more familiar with the kinds of things that can cause screw-ups than Linux ones?

**Edit:**

I may as well mention this now, just in case you resort to something drastic before posting back. Assuming you have enough free disk space lying around to do so, you should consider doing a disk dump of your NTFS partition. Basically, I'm imagining a worst case scenario, where you convince yourself today that saving your files is a lost cause, only to discover tomorrow that it's actually quite easy! By dumping the drive contents byte for byte, you could reclaim the disk *and* hold onto the data in case (a) you do something to make things worse, or (b) you find a solution to your problem in two weeks' time.

---

### Post by samssf on 2006-09-20
Thanks again for the help...

I think I've figured out what happened. I installed Grub into the boot sector of my NTFS partition. This happened because I have a Raid setup and some other crap that confused me (I had trouble with the 64bit version but installed grub onto the EXT3 partition and got it to work... long story)

That NTFS partition wont boot since it will just reload grub. Next thing I will try is a windows XP CD to use fixmbr command and see what happens. Or just reinstall xp =(

I need to fix this so that I can boot to windows as well as mount that NTFS partition in Ubuntu... or just call it a loss.

---

### Post by samssf on 2006-09-21
Ok, so I decided to try what was suggested to me and try NTFSTools to see if I could figure anything out. To my dismay, NTFSTools told me that my NTFS partition is unreadable and I should use chkdsk. Damn.

So I boot using the windows xp cd, and ran chkdsk. Chkdsk told me:

"Disk appears to have unrecoverable problems" or something like that.

so I decided to run the Fixboot command. When I did, it said
"Cannot read filesystem on C:".... do you wish to try to fix the boot record? I said yes. Then it says

"Attempting to detect filesystem...filesystem detected as NTFS"
"Attempting to rewrite boot sector to C:.... success"..

So then I run chkdsk again, and it says everything is fine!
I boot to linux, and behold, my NTFS partition mounts immediately. All I had to do was go to "Computer" and double click on the drive.

Thanks for everyone who helped think about a solution.

---

### Post by kidders on 2006-09-21
Fantastic news!

---

