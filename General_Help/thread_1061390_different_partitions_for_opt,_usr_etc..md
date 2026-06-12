---
title: "different partitions for /opt, /usr etc."
date: 2009-02-05
forum: General Help
---

### Post by cheics on 2009-02-05
I have a eeepc and had installed ubuntu with / mounted to the fast internal 4GB partition and /home mounted to the 16GB slow(er) internal partition

I ran out of space on / today and have seen setups with /usr, /bin, /opt etc. mouted on different partitions.

1.)
Which ones would would have the smallest effect on the speed of the laptop while doing things such as browsing and possibly freeCiv ;)

2.) is there a way to move the partitions without reinstalling ubuntu??

Thanks in advance

---

### Post by mb_webguy on 2009-02-05
For a desktop, there's really no reason to have separate partitions for directories other than /home.  This is done on servers for various reasons, none of which really apply to desktops.

And assuming that your two partitions are on the same drive, there shouldn't be any differences in speed.  Adding more partitions wouldn't have any effect on the apparent speed of your system, unless they were added to a different, faster drive.  And even then, it would only increase the speed of things directly involving reading or writing to the drive.  It might possibly make programs load slightly faster, but it won't make them run faster.

---

### Post by cheics on 2009-02-05
right now / is on the small fast drive... it is now full :(

I would move the whole partition to the larger slower drive if it were not slower...

I want to move as much as I can to the slower drive, w/o slowing down the overall system

I also need to know how to move the partitions w/o a reinstall

---

### Post by mb_webguy on 2009-02-05
If that's the case, then use Disk Usage Analyser to identify which system directory is taking up the most space.  In my case, it's /usr at just under 3GB.

Boot up a LiveCD and use GParted (System->Administration->Partition Editor) to shrink your /home directory and otherwise make room for the new partition on the second drive.  It of course needs to be at least as big as the directory you want to move to it.  Make the new partition and format it as ext3 (or your favorite Linux filesystem).

Now exit the partition manager and mount the new partition and your / partition.  Copy all of the files from the directory you want to move to the new partition.  You need to make sure you maintain the owner and permissions when you copy, so use "cp -Rp" in the terminal.  Now edit the /etc/fstab on your / partition and add an entry for the new partition, with the mount point, UID, GID, and permissions corresponding to the directory you're moving.  You need to use the UUID rather than a symlink, so get the UUID for the partition with the command "sudo blkid".  Verify that everything has been copied.  Now rename the original directory to something the system won't recognize, such as by appending "_old" to the directory name.

If you've done everything correctly, when you reboot, the system will mount and use the new partition in place of the old one.  (If you did something wrong, it should be pretty obvious.  Reboot the LiveCD and figure out where you goofed.)

Good luck.

---

### Post by dcstar on 2009-02-05
> **cheics said:**
> I have a eeepc and had installed ubuntu with / mounted to the fast internal 4GB partition and /home mounted to the 16GB slow(er) internal partition

I ran out of space on / today
........

Then clean out your downloaded package cache and the problem will go away.

---

### Post by cheics on 2009-02-06
> **mb_webguy said:**
> If that's the case, then use Disk Usage Analyser to identify which system directory is taking up the most space.  In my case, it's /usr at just under 3GB.

Boot up a LiveCD and use GParted (System->Administration->Partition Editor) to shrink your /home directory and otherwise make room for the new partition on the second drive.  It of course needs to be at least as big as the directory you want to move to it.  Make the new partition and format it as ext3 (or your favorite Linux filesystem).

Now exit the partition manager and mount the new partition and your / partition.  Copy all of the files from the directory you want to move to the new partition.  You need to make sure you maintain the owner and permissions when you copy, so use "cp -Rp" in the terminal.  Now edit the /etc/fstab on your / partition and add an entry for the new partition, with the mount point, UID, GID, and permissions corresponding to the directory you're moving.  You need to use the UUID rather than a symlink, so get the UUID for the partition with the command "sudo blkid".  Verify that everything has been copied.  Now rename the original directory to something the system won't recognize, such as by appending "_old" to the directory name.

If you've done everything correctly, when you reboot, the system will mount and use the new partition in place of the old one.  (If you did something wrong, it should be pretty obvious.  Reboot the LiveCD and figure out where you goofed.)

Good luck.

In my case /usr is the largest; however, is it the partition I should be moving to my 'slow' drive?

And thanks for the prompt reply

---

### Post by mb_webguy on 2009-02-06
Your /usr directory contains your applications.  The only time these files are read is when you run an application, and then only until the application is loaded into memory.  Putting /usr on the "slow" drive might result in a slightly longer load time for applications, but unless you're starting a very large application and your "slow" drive is very, very slow, it shouldn't be a noticeable difference.

---

### Post by jocko on 2009-02-06
The first thing I would move (after /home) is /var.
The size of /var is quite variable, as apt/synaptic saves downloaded packages in /var/cache/apt/archives/.
When I clean out my downloaded packages /var is only about 300 Mb, but it can be up to several Gb and needs free space for apt/synaptic to work properly, so moving /var to it's own partition is probably a good idea if you have a limiting amount of space.
I don't think moving /var to a slower disk will slow down any part of your system, whereas moving anything else will probably have some effect (although the effect may not be noticeable...).
I think after you have moved /var, the size of the rest of the / file system will probably be very stable, so you may not need to move anything else unless you want to install some software that needs lots of space.
You may also get rid of a few hundred Mb by uninstalling some things you never use (just be careful to see which packages are removed together with what you uninstall).

---

### Post by mb_webguy on 2009-02-06
Jocko has a good point about putting /var on a separate partition to limit its size.  This is the primary reason that most servers have a separate /var partition -- this is where logfiles and webserver files go, and those can both fill up a partition pretty quickly (the latter especially on a web server hosting a message board that allows file uploads).  

On the other hand, while /var can potentially become very large, it's less likely to do so on a desktop, and it's also the easiest directory to clean.  And the fact that it is variable in size makes me hesitant to suggest putting it on its own partition on a desktop system.  If you keep /var cleaned out, by putting it on a separate partition of any decent size you'd be wasting space that could otherwise be devoted to something more useful.

It's really up to you to decide what's best for your system based on your user habits.

---

### Post by jocko on 2009-02-06
> **mb_webguy said:**
> Jocko has a good point about putting /var on a separate partition to limit its size.  This is the primary reason that most servers have a separate /var partition -- this is where logfiles and webserver files go, and those can both fill up a partition pretty quickly (the latter especially on a web server hosting a message board that allows file uploads).  

On the other hand, while /var can potentially become very large, it's less likely to do so on a desktop, and it's also the easiest directory to clean.  And the fact that it is variable in size makes me hesitant to suggest putting it on its own partition on a desktop system.  If you keep /var cleaned out, by putting it on a separate partition of any decent size you'd be wasting space that could otherwise be devoted to something more useful.

It's really up to you to decide what's best for your system based on your user habits.
You say /var is not likely to become *very* large on a desktop, but... all is relative. If /var is on a *very* small partition, you don't need to run a server to fill it up...
If you have your / file system on a drive that is only 4 Gb, it's very likely that you need to empty the apt archives very often (= after each update) or even setting apt to automatically delete packages immediately after install.
It may even happen that a large upgrade (such as going from one ubuntu release to the next, which require at least around 800 Mb, but probably more than 1Gb of free space) can not be completed, as it will fill up the hard drive with packages during the actual install process.

---

### Post by mb_webguy on 2009-02-06
But that's pretty much what I was saying.  The size of the /var is very variable.  Putting it on a partition too small may prevent you from doing certain things (like a full upgrade), but putting it on one too large is a waste of space, particularly if you keep it fairly clean (which you can set to be done automatically).

It seems to me to be a better use of resources to move a directory of a more stable size on a separate partition, and keeping /var under the root partition.  That way you're not wasting a partition solely on /var, when that directory may rarely use more than a fraction of the partition.

---

### Post by cariboo on 2009-02-06
I would suggest doing what dcstar said and clean out the package cache in /var/cache/apt/archives. Open a Applications-->Accessories-->Terminal and type at the prompt

```
sudo apt-get autoclean
```

and just in case

```
sudo apt-get clean
```

I wouldn't bother with creating seperate partitions for any of the directories. You will lose 5% of each partiton you create to the root user so that it can still function when you run out of hard drive space. With only 4Gb for /root you will lose a total of 200Mb and with a full install taking about 3Gb that doesn't leave a lot of room for a package cache or /tmp.

Jim

---

