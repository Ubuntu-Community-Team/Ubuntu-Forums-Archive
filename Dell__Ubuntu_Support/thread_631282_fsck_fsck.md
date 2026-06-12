---
title: "fsck fsck"
date: 2007-12-04
forum: Dell  Ubuntu Support
---

### Post by larryhowe on 2007-12-04
Whoever came up with the idea of forcing a fsck check after a certain number of mounts, while giving the user no choice in the matter: Thanks a lot. I am working from home today, and I got up early, got all my stuff ready, booted my PC...and now I'm sitting here watching fsck.

It is sitting there stuck at 54.6%, hasn't moved in 10 minutes. The check started 20 minutes before that. I only know from experience, from this ******* thing having screwed me over once before, that it will eventually complete after an hour or so. I apologize for storing video on my hard drive, that's probably what's taking so long.

Did anyone ever think that setting up an automatic Denial of Service attack, that the user can't control, might be a bad idea? Did anyone think about this at all before they did it? 

I have other thoughts on this matter but they aren't appropriate for a family oriented forum such as this.

Oh but hey, I'm overreacting, in the time it took me to write this it's now at 55.9%, so this should be done after lunch, only wasting my entire morning.

Larry

---

### Post by saru411 on 2007-12-04
there are ways of changing the amount of boots until fsck runs. im not saying it wouldnt be nice if it asked you before preforming the fsck but this is one option to help reduce how often it scans.

---

### Post by dca on 2007-12-04
You can turn the function off in 'fstab' but it's not recommended...

---

### Post by Dennis N on 2007-12-05
So that you won't be surprised by this happening at an inconvenient time, you can check when it will happen by typing "sudo showfsck" in the terminal.

---

### Post by sciurus on 2007-12-07
Use *tune2fs -c* to adjust the number of mounts between fscks,

---

### Post by johnw2007 on 2007-12-12
There is an excellent way to control fsck at [https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck). It allows you to set the frequency and call fsck at shutdown instead of startup.

---

### Post by Mud.Knee.Havoc on 2007-12-13
I have mine set to fsck upon every boot.  That's just because my uptime is in the weeks/months, so if it goes down, it's because something bad happened. :D

---

### Post by larryhowe on 2008-02-14
Just got burned again!!

I installed autofsck which is better except it now prompts me whether to fsck on every shutdown. Today I had to kill the X server, so no chance to say Cancel. So when it rebooted...fsck.

So here is my workaround to this problem:

su -
mv /sbin/fsck /sbin/fsck.denial.of.service

Hope this gives me some relief from this nightmare that is fsck.

I wish whoever set this up like this could sit through every painful second of waiting for it to finish.

---

### Post by neptho on 2008-02-15
This is not wise; you should not move fsck, or you should update to a filesystem where you are not blocked.  Reiser, JFS, and ext3 can do most fscking in the background.

Do as mentioned above, and use tune2fs -c (mount count) on your partitions to raise the maximal mount count; moving and renaming fsck will only eventually bite you.

---

### Post by articpenguin on 2008-02-20
no filesystem runs fsck in the background.

Ext3 is a safety filesystem that writes to the disk every 5 secs, and forces fsck every 20 mounts or so.

JFS ricerfs and XFS dont force fsck as they are the TRUE journalling filesystems.

---

### Post by jrusso2 on 2008-02-20
This is why ext3 is not good.  can you imagine having to reboot a large server and have it time to do fsck.

Its better to use a more modern filesystem. Hopefully Linux will come up with a good replacement, besides ext 4

---

### Post by articpenguin on 2008-02-22
Btrfs

---

### Post by larryhowe on 2008-02-23
I finally tamed autofsck with some help from the author. Had to run this:

sudo fdisk -l

to see what devices are being mounted, and then

tune2fs -C 0 /dev/sdax

where sdax = sda1, sda2, etc....all the devices that show up under fdisk.

I'll have to see how it goes from here.

This entire situation could have been avoided if the fsck authors made it so it gives us some kind of warning before taking over the PC. Like a 10-second "Press any key to cancel", or the ability to ctrl-C out of it, or something. I promise, I'll be a good boy and let fsck run from time to time, if you just give me the ability to have some control over my PC.

---

### Post by ChaosParser on 2008-02-24
> **larryhowe said:**
> 
This entire situation could have been avoided if the fsck authors made it so it gives us some kind of warning before taking over the PC. Like a 10-second "Press any key to cancel", or the ability to ctrl-C out of it, or something. I promise, I'll be a good boy and let fsck run from time to time, if you just give me the ability to have some control over my PC.

You'll be pleased then, to hear that Hardy has a cancel option.  Just wait. :)

---

