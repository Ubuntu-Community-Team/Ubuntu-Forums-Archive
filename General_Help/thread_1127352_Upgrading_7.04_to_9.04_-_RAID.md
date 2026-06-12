---
title: "Upgrading 7.04 to 9.04 - RAID"
date: 2009-04-16
forum: General Help
---

### Post by BrightEyesDavid on 2009-04-16
Hi there,

The Ubuntu machine I use as my test web server currently runs 7.04 and was never updated to the most recent updates. When I try to update now using Update Manager I get:

```
W: Failed to fetch http://security.ubuntu.com/etc.etc.deb
  404 Not Found
```Update Manager shows me a 'New distribution release '7.10' is available' notification with an appealing looking 'Upgrade' button next to it, but I remember reading that this shouldn't be done before ensuring 7.04 is up to date. Any advice?

I'm rather worried about upgrading in general as I have a lot of data across the four disks in RAID5:

/dev/sda1 500MB /boot
/dev/sdb1 500MB /boot
/dev/sdc1 500MB swap
/dev/sdd1 500MB swap
/dev/sda2 500GB /
/dev/sdb2 500GB /
/dev/sdc2 500GB /
/dev/sdd2 500GB /

And this leads me to the following question: if I can't automatically upgrade via Update Manager (I would prefer a clean install in some ways), how do I install 9.04 when it is released without loosing the RAID setup and the data I have in '/data' which is across RAID5?

Many thanks.

---

### Post by BrightEyesDavid on 2009-04-16
> **BrightEyesDavid said:**
> And this leads me to the following question: if I can't automatically upgrade via Update Manager (I would prefer a clean install in some ways), how do I install 9.04 when it is released without loosing the RAID setup and the data I have in '/data' which is across RAID5?
I've been thinking...

To avoid this kind of issue in the future, what do you think of me copying everything off onto external hard drives and repartioning the four drives, freshly installing Ubuntu and arranging the OS to go onto non-RAID drive space and only my data (which is the important thing) to go onto RAID drive space?

Hopefully this wouldn't be too difficult for a relative novice like myself, and would mean that I wouldn't have to worry about my data being on the filesystem partition. No?

Any insight appreciated as I'm confused about how to proceed long term. I want to be able to upgrade Ubuntu.

---

### Post by cariboo on 2009-04-16
It would probably be better to do a clean installation, as you would have to follow this upgrade path, 7.04-->7.10-->8.04.2-->8.10-->9.04.

You don't have to repartition, when you get to the partitioning section, just mark the partitions to be formatted. Be sure to back up your important data first.

Jim

---

### Post by BrightEyesDavid on 2009-04-16
Thanks for the reply.

> **cariboo907 said:**
> You don't have to repartition, when you get to the partitioning section, just mark the partitions to be formatted. Be sure to back up your important data first.

But if the contents of the current filesystem are currently on the software RAID5 partitions, won't this cause an issue?

If I started again with the partioning, I could use RAID only for data and /home and keep the OS/filesystem away from it... I think.

---

### Post by BrightEyesDavid on 2009-04-17
I realised I never stated that this is *software* RAID.

To clarify/update my idea: I'm thinking that it might be good for me to run Ubuntu itself from a separate RAID array, for example:

```
**RAID 1**
/dev/sda1 500MB /boot
/dev/sdb1 500MB /boot

**non-RAID**
/dev/sdc1 500MB (swap)
/dev/sdd1 500MB (swap)
[B]
RAID5[/B]
/dev/sda2 5GB /
/dev/sdb2 5GB /
/dev/sdc2 5GB /
/dev/sdd2 5GB /

**RAID5**
/dev/sda3 500GB /data
/dev/sdb3 500GB /data
/dev/sdc3 500GB /data
/dev/sdd3 500GB /data
```Am I right in thinking that this kind of arrangement would (after a new partitioning, OS install and RAID array setup) solve my current issue of having my data on the same array as my non-upgradeable Ubuntu OS? As I see it, I would be free to format and reinstall Ubuntu in future without touching the partitions that contain my data, which would mean that I could recreate the /data array after doing so whilst keeping the data on it across the four partitions/disks.

Your advice and thoughts would be appreciated.

---

### Post by BrightEyesDavid on 2009-04-19
So what do you reckon on my idea? Setting up software raid from the alternative installation CD doesn't sound too hard...

---

### Post by fjgaude on 2009-04-19
> **BrightEyesDavid said:**
> So what do you reckon on my idea? Setting up software raid from the alternative installation CD doesn't sound too hard...

I take it you would make your boot partition a raid1 array?

After using software raid, **mdadm**, for a number of years I go with a separate boot drive, a fast one, and then have all my data on a four-drive raid5. That has worked fine, along with triple backup of the raid5, one online, one near-line, and one off-line.

---

### Post by BrightEyesDavid on 2009-04-20
> **fjgaude said:**
> I take it you would make your boot partition a raid1 array?

After using software raid, **mdadm**, for a number of years I go with a separate boot drive, a fast one, and then have all my data on a four-drive raid5. That has worked fine, along with triple backup of the raid5, one online, one near-line, and one off-line.
Yeah, /boot would be RAID1 as per my last idea. I'll stick to using just the four drives which are already in the PC as I don't want to be fiddling in there right now.

So I guess I've got to the stage where I know what I want to do. Hopefully it will go okay if I follow guidelines. Will start copying off all my data...

---

