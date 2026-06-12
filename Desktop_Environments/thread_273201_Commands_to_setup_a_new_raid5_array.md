---
title: "Commands to setup a new raid5 array?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by wkulecz on 2006-10-07
I installed Ubuntu 6.06.1 alternate install CD to a raid1 array without issues, using it to write this.

In short, what commands did the installer use to setup the array and how do I duplicate it?

I've used fdisk to create entire disk partitions marked type fd on hde1, hdf1, hdg1, & hdh1.  How to proceed now leaves me confused at best after using the search and finding mostly stuff about 5.10 and raidtools.

It seems clear mdadm was used and my fstab is md0 ext2 \, md1 swap, so I'd be fine creating a raid5 md2 and mounting it where I want.  I'd prefer xfs filesystem for this, question is what do I do next?

--wally.

---

### Post by wkulecz on 2006-10-09
Found this via google:
 [http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID#Set_up_partitions](http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID#Set_up_partitions)

Most linux docs about raid assume the distro uses raidtools which are *not* part of Ubuntu.  The installer knew what to do automatically, but by default mdadm (which is used instead of raidtool) docs were not installed. (I'm not sure what doc package had them, I just went nuts installing things in the doc tree with Synaptic).

The Gentoo recipe seems to be working, althouh its going to take about 2.5 hrs to "sync" the array (4 250GB drives in a default raid5 setup) before I can do mkfs and mount, not sure what is going on here that is so time consuming.

--wally.

---

### Post by wkulecz on 2006-10-10
Anyone know why two raid5 entries ended up in my mdadm.conf file?  All seems to work so I ain't worried, but it was unexpected, but then pretty much all the docs/examples I've found talk about raid0 or raid1 setups.

mdadm.conf
ARRAY /dev/md4 level=raid1 num-devices=2 UUID=94427244:e6d5eaca:dc919faa:6810eb25
ARRAY /dev/md3 level=raid5 num-devices=4 UUID=88f09cb4:b3e74e61:c11d9428:965d1d62
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=88f09cb4:b3e74e61:c11d9428:965d1d62
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=8a13a9d8:b1be8465:6f7316d0:f8c10530
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=cde3fd73:db721147:ae9dc413:29341393



here is what /proc/mdstat has to say
Personalities : [raid1] [raid5]
md4 : active raid1 hdc3[1] hda3[0]
      236388352 blocks [2/2] [UU]

md3 : active raid5 dm-5[3] dm-4[2] dm-3[1] dm-2[0]
      732587712 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md2 : active raid5 hde1[0] hdh1[3] hdg1[2] hdf1[1]
      732587712 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md1 : active raid1 hda2[0] hdc2[1]
      7815552 blocks [2/2] [UU]

md0 : active raid1 hda1[0] hdc1[1]
      48829440 blocks [2/2] [UU]

unused devices: <none>


I created md3 and md4, md0 and md1 were created by the alternate install and I had planed to put md4 at md2 after I created the raid5 but an md2 appeared automagically!

--wally.

---

### Post by wkulecz on 2006-10-10
Real bad news, the raid1 appears to be working correctly.  The raid5 is corrupting all data I copy to it!  I tried xfs and ext3.

No idea what to do next.

--wally.

---

### Post by wkulecz on 2006-10-11
I tried creating a raid1 on these two drives and also got corrupt data when I tried to copy to it.  Then tried ext3 on a single drive and still got corrupted data!!

I doubt all drives are bad, so at this point I suspect the problem is with the SIL680 "medley" fakeraid controller.  It had worked under windows, I was not using "fakeraid", just treating it like a normal ide controller since the kernel picked it up as ide2 & ide3, I expected it to work :(

I'm out of time.  Can get by with everything on the raid1 array on hda & hdc for a few months while I sort this out and maybe try a different PCI ata100 controller or some ide to sata converters.

--wally.

---

