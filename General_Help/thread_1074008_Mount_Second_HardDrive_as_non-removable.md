---
title: "Mount Second HardDrive as non-removable?"
date: 2009-02-18
forum: General Help
---

### Post by Epidural on 2009-02-18
Hey there. I switched to Ubuntu, love it, don't regret it never will. xD But I've been living with this tiny annoyance.

When I first partitioned and formatted my HDDs, I mounted a 10GB partition as /home/music/ , this way I can save this partition no matter how much I mess with the boot and home partitions without having to re-load 8 gigs of music.

However, I seem to have at some point unmounted that 10GB partition, and when I re-mounted it, it shows up as a removable drive, much like a jump/flash/thumb-drive would. It IS mounted at /home/music/ (I have no "music" folder made by ubuntu, just the partition, exactly how I want it).

This "removable drive" display method ANNOYS ME, though. I end up unmounting this partition instead of my jump-drives or something stupid like that. I've googled around for a solution, but if there was one, I couldn't narrow my search properly enough to find it.

So my question is; How do I mount my 10GB Music partition to /home/music/ WITHOUT it showing up as a removable drive?


Thanks in advance for your replies.

---

### Post by cariboo on 2009-02-18
You can have it automount in /etc/fstab eg:

```
/dev/sdb1  /home/music ext3 realatime  0   2
```

You can also mount the drive using uuid instead of a device label eg:

```
# Second internal drive mount as /home/stoage
UUID=909c15ad-6d56-4cca-aa87-3f9289c79dad /home/storage	 ext4     relatime        0       2
```

The above example is how I mount my 2nd internal drive.

To find your hard drives's uuid in a terminal type:

```
blkid
```

the result should look something like this:

```
/dev/sda1: UUID="909c15ad-6d56-4cca-aa87-3f9289c79dad" TYPE="ext4" 
/dev/sdb1: UUID="B0C07D4DC07D1AB4" TYPE="ntfs" 
/dev/sdb2: UUID="e44c6e62-f018-4e73-926f-b8f51860f2c9" TYPE="ext4" 
/dev/sdb3: UUID="fd99f97b-4c48-7ab0-ff17-4a32076f932c" TYPE="swap" 
/dev/sdb4: UUID="16ba3cd0-406e-46ee-ba5e-d147f4bcb073" TYPE="ext4"
```

Jim

---

### Post by Epidural on 2009-02-18
I've got it set to auto-mount when Ubuntu boots, that isn't a problem. I'll include a copy of my fstab in case it helps anything further, but my problem isn't auto-mounting.

The problem is, however petty it may seem, the music partition SHOWS UP as a removable drive instead of just 'being' /home/music/. When I first installed ubuntu, this is how it was; No icon on my desktop was appearing.

My /home/ folder is also a seperate partition, and does not show up as a removable drive. It just sits quietly as my /home/ folder as I want it to.

However the /home/music partition got un-mounted accidentally at one point, and since then I havn't been able to mount it how it was. It is mounted, works, reads/writes/executes, but it doesn't hide itself as just part of my file system, it sticks out as a removable drive and I end up messing with it unintentionally.

So... how the heck do I tell it to hide away like my home folder is doing?


My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=05313095-e88b-4cff-8c3e-9f0c84dce203 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=9f816d07-881d-4053-ac57-a30f57e503c0 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=e3177a44-a1ee-474f-9b08-4ef4b5b72926 /home/mitch/Music     ext3    relatime       0       2
# /dev/sda5
UUID=81676f76-abba-468e-b93a-8288a227aca5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Epidural on 2009-02-19
bumpp.

If it's for whatever reason only possible to mount it like I want it when you first set-up your drives using the installation partition editor/mounter, then I'd appreciate hearing that. Disappointed, but it would be greatly appreciated.

Thanks again.

---

