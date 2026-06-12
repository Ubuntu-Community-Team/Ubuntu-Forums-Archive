---
title: "Help Rebuiding Software RAID Array Please"
date: 2009-01-18
forum: General Help
---

### Post by mattwynne on 2009-01-18
Hi,

I've had a RAID array running fine for about 6 months, but just recently it stopped working. The machine won't boot, and instead gives the following error:

> ALERT! /dev/md2 does not exist. Dropping into a shell!

For some background, I have 4 identical drives, bought seperately, each with four partitions in an identical pattern.

These are (or rather were) then combined into the following RAID configuration:

/dev/sda1 + /dev/sdb1             = 50MB   RAID 1 (boot)
/dev/sda2 + /dev/sdb2             = 1000MB RAID 1 (swap)
/dev/sda3 + /dev/sdb3 + /dev/sdc3 = 20GB  RAID 5 (/)
/dev/sda4 + /dev/sdb4 + /dev/sdc4 = 480GB RAID 5 (/home)

/dev/sdd3 and /dev/sdd4 were marked as spare for the root and home RAID arrays.

I've done some digging around with fdisk and mdadm using a LiveCD to get some idea what's gone wrong, but I'm nervous to actually do anything to the arrays without getting some advice here. I'm relatively new to linux and this is definitely pusing me outside my comfort zone! I have an old backup of the data, but it's personal stuff like family photos, so I want to be extra-careful.

Using mdadm --examine, I've figured out that, as you might expect, the two smaller (boot / swap) partitions are fine. The problems are with the larger two, and seem to centre around /dev/sdc.

I've attached the output from mdadm --examine /dev/sd* but to summarise, it looks a little like this:

  * sda & sdb both think that sdc has failed on partitions 3 & 4
  * sda & sdb are in good shape, but not aware of a spare
  * sdc thinks it's OK, though it also thinks that something else has failed on partition 4
  * sdd doesn't know anything's wrong

So it seems as though the superblocks have become corrupted, as they don't seem to contain consistent information. I'm not sure what my next step should be. I'm pleased to see that only /dev/sdc appears to have actually failed, but I'm not sure how best to try re-attaching /dev/sdd's spare partitions to the arrays - I had hoped this would just happen by magic when there was a problem!

What should I try next?

---

### Post by fjgaude on 2009-01-19
Wow, you have an interesting setup, and very useful, if we only knew the exact procedures to follow when things go wrong, when a partition fails, when a whole drive fails.

Can you tell us if you followed some HOW-TO to get to where you are?

I'd try this first before doing anything else. Remove or rename the **/etc/mdadm/mdadm.conf** file, using **apt-get** remove **mdadm**, and reboot. Then somehow getting back to the OS I'd reinstall mdadm and run this command:

```
sudo mdadm --assemble --force --scan
```

A new mdadm.conf file will be auto-created. From there I'd run these:

```
suod mdadm -D /dev/md[n]
```

for each of the three or so arrays.

If this way doesn't work, I'd think about removing a drive through faulting it with mdadm and adding back a spare that has been correctly partitioned.

Let us know what going on, please.

---

### Post by mattwynne on 2009-01-20
Hi fjgaude,

I haven't followed any HOWTO, no. I did follow a couple of guides some time ago to set up the array originally, and I can probably find them again if you think it's relevant.

I'm not sure how I should do what you've suggested. I can boot the machine on a live CD, but that doesn't come with mdadm by default, so I have to install it (using apt-get) anyway.

How can I access the /etc/mdadm/mdadm.conf file being used by the machine when it tries to boot from the hard-drive?

Or can I run the commands you've suggested from the 'initramfs' prompt that comes up when the machine fails to boot?

Thanks for taking the time to help.

---

### Post by fjgaude on 2009-01-20
Gosh... I'm beginning to see what the real issue is.

Somehow from a command prompt, you have to get over to the **mdadm.conf** file, re-name it, and then remove **mdadm**, again from command line using **sudo apt-get remove mdadm**.

When you boot up, can you not use the (recovery mode) version of the OS, the second line of the grub prompt? That has an option for a normal command line at the end of its running through all the loadings.

---

### Post by mattwynne on 2009-01-20
The OS itself is installed on one of the RAID devices:

> /dev/sda3 + /dev/sdb3 + /dev/sdc3 = 20GB RAID 5 (/)

Surely if I delete the md configuration, it's not going to be able to boot at all, because all the OS stuff is on a RAIDed partition, right?

How do I bring up the grub prompt?

---

### Post by fjgaude on 2009-01-21
First off the kernel **md** uses the array UUID to assemble. The **/etc/mdadm/mdadm.conf** file is not necessary and gets auto created if you do as I suggested above.

Look this over and see if anything there is useful:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

What you have here is a very complex system and when things go wrong we have to use detective ways to find out how and what is wrong. Not an easy task and is why few have done what you have done.

Let us know how things are going.

---

### Post by mattwynne on 2009-02-01
I fixed it.

Here's how I did it, in case anyone else comes across the same problem.

First I shut down the machine and removed drive /dev/sdc which seemed to be the root of the problem by unplugging it.

I booted the machine as normal, and when I got dumped out to the initramfs prompt, I ran some mdadm commands to rebuild the array.

Since I'd removed /dev/sdc, the disk with the spare partitions on it, formerly /dev/sdd had now become /dev/sdc. I needed to add those partitions back into the array manually.

For example:
```
mdadm --add /dev/md2 /dev/sdc3
```

Now, to find out the status of the array:
```
cat /proc/mdstat
```

Happily, when you add the spare partition back into the array, mdstat shows a progress bar as the array rebuilds. Success!

Finally, I shut-down again, removed all the drives but the broken one, and ran the manufacturer's SMART diagnostics CD on the drive to check for defects. It passed, suggesting that the only problem I'd ever had was superblock corruption. I wonder how that happened?

A concept I had not understood at the time, was that there are effectively two boots that happen when you are using software RAID to hold your root partition. It's obvious with hindsight, but before that root partition can be read, the /boot partition loads a small 'initial RAM file system' linux kernel which knows about software raid, and can then assemble and read the RAIDed root partition to do the main boot. So when you find yourself at the initramfs prompt, you're at the prompt for that little boot kernel. Since this is stored in an image, I'm not sure there is any way to modify it's files as fjgaude suggested, although it might be possible if you were in a liveCD and could regenerate the /boot/initrd.img file.

Hope that helps someone. Now to figure out how to do some automatic monitoring of the array so this doesn't happen to me again...

---

### Post by fjgaude on 2009-02-02
Glad you got it up and running again... we learn things as we go along, eh?

---

