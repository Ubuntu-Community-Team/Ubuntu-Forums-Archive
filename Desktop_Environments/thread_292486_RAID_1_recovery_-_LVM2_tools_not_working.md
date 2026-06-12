---
title: "RAID 1 recovery - LVM2 tools not working"
date: 2006-11-03
forum: Desktop Environments
---

### Post by kalahari875 on 2006-11-03
I thought that when I installed my Dapper system and got it installed on mirrored RAID 1 drives that I was doing myself a favor... until a drive got corrupted somehow, the corruption got mirrored to both drives, and Kubuntu would no longer boot. I unmounted the filesystem and ran fsck to repair errors, but apparently some files are crippled beyond recognition and the system won't start even for me to get a terminal. Now I'm struggling to get the data off of one of the mirrored drives.

I need to solve one or both of two problems: 

1) Is there a way to perform a "repair reinstallation" with Kubuntu Dapper so that the system files can get repaired and I can potentially get the thing to boot _without wiping out all of my configuration files_ for installed programs (such as BIND and Postfix)? One of the things I want to recover is that set of configuration.

2) If not, can someone please help me mount and recover data from the dead mirror? I've been trying this using [these instructions]("http://www.linuxjournal.com/article/8874"). I took one of the mirrored drives and stuck it in a non-mirrored Ubuntu Edgy box. I can see the mirror via the mdadm --scan commands listed and was able to create a new mdadm.conf.  After activating the array, /proc/mdstat contains:

[INDENT]md2 : active raid1 hdb6[1]
[INDENT]19004736 blocks [2/1] [_U][/INDENT]

md1 : active raid1 hdb5[1]
[INDENT]979840 blocks [2/1] [_U][/INDENT]

md0 : active raid1 hdb1[1]
[INDENT]48064 blocks [2/1] [_U][/INDENT]
[/INDENT]

However, after that I get lost. The article mentions running vgchange -a y to try to recover the LVM2 volume in the RAID array. I installed lvm2 on the Edgy box, but issuing vgchange -a y only reports "No volume groups found." I tried issuing:
[INDENT]dd if=/dev/md2 bs=512 count=255 skip=1 of=/tmp/md2-raw-start [/INDENT]
to extract the LVM2 configuration from the media, but I have ONLY binary data--no recognizable text is embedded in the extracted sectors, so I can't see any configuration text to retrieve.

Since I don't have a backup of the configuration, and can't see it on the source disk, how can I recreate the lvm configuration? ](*,) 

Thanks in advance.

---

