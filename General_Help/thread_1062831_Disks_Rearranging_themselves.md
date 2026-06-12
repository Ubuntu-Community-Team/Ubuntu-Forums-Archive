---
title: "Disks Rearranging themselves"
date: 2009-02-07
forum: General Help
---

### Post by highgeere on 2009-02-07
I hope that this isn't some well known or commonly discussed issue, as I wasn't able to find any other threads describing the symptoms I'm having. I have a Gigabyte GA-MA770-DS3P motherboard on which I am using 5 sata drives of various sizes. Each drive is standalone. One is entirely ntfs, one is split up into 4 partitions(one ntfs, one swap, two ext3), and the remaining three are each one ext3 partition. 

I have been having this issue recently where upon boot the drives are no longer associated with the previous /dev/sdx identifier. So for example, originally I had sda2 mounted as / and sda4 mounted as /home. It dropped me to a root shell during boot, and I found that /home was not able to be mounted because /dev/sda4 didn't exist. It was able to boot to that point because /dev/sda2 had been replaced with UUID=some-numbers in /etc/fstab. The drive that had formerly been sda was now sdd, and the other drives were also moved around in what appeared to be a random way. 

Has anyone else encountered this behavior, and is there something about my board or configuration that would cause this?

---

### Post by jocko on 2009-02-07
> **highgeere said:**
> I hope that this isn't some well known or commonly discussed issue, as I wasn't able to find any other threads describing the symptoms I'm having. I have a Gigabyte GA-MA770-DS3P motherboard on which I am using 5 sata drives of various sizes. Each drive is standalone. One is entirely ntfs, one is split up into 4 partitions(one ntfs, one swap, two ext3), and the remaining three are each one ext3 partition. 

I have been having this issue recently where upon boot the drives are no longer associated with the previous /dev/sdx identifier. So for example, originally I had sda2 mounted as / and sda4 mounted as /home. It dropped me to a root shell during boot, and I found that /home was not able to be mounted because /dev/sda4 didn't exist. It was able to boot to that point because /dev/sda2 had been replaced with UUID=some-numbers in /etc/fstab. The drive that had formerly been sda was now sdd, and the other drives were also moved around in what appeared to be a random way. 

Has anyone else encountered this behavior, and is there something about my board or configuration that would cause this?
The only way to mount disks that is totally consistent between boots is by only referring to them by their uuid in /etc/fstab (as the /dev/sdX designations are pretty randomly assigned on each boot). This is the way it has been in ubuntu for a few years now.
Just find the correct uuid:s for all your partitions:
```
ls -l /dev/disk/by-uuid/
```
This will list all partitions in this format:
```
lrwxrwxrwx 1 root root 10 2009-02-07 00:17 [COLOR=Blue]0e305a79-d82d-4979-b8a7-764ea161a7fa[/COLOR] -> [COLOR=Red]../../sda5[/COLOR]
```where [COLOR=Blue]0e305a79-d82d-4979-b8a7-764ea161a7fa[/COLOR] is the uuid and [COLOR=Red]../../sda5[/COLOR] is the device node for the same partition **on this particular boot**.
Make sure you know which line in fstab is for which partition (as the /dev/sdXY part may be different from the ../../sdXY what you got from 'ls -l /dev/disk/by-uuid/'), and simply replace the "/dev/sdXY" part with "UUID=" and the correct uuid.

---

### Post by drs305 on 2009-02-07
Another option, in keeping with the idea that you don't want to list things in fstab as *sdXX*, is to label the partitions and mount them via their label. Labels are a bit more descriptive than the UUIDs. Another advantage is the label name will appear in nautilus when the partition is mounted (instead of "52.5 GB Media", for instance).

Each type of filesystem has its own commands for labeling, but *gparted* can label most of them. Once a partition has a label, instead of "UUID=XXXX" you substitute "LABEL=XXXXX". 

Since in *gparted* the partition has to be unmounted to label it, you can label your system partitions with:
```

sudo tune2fs -L [COLOR="DarkRed"]any.label.name[/COLOR] /dev/sd[COLOR="DarkRed"]XX[/COLOR]  # Example: sudo tune2fs -L mydata /dev/sdb2

```

---

### Post by highgeere on 2009-02-07
Thanks guys. I have never had more than 3 standalone disks at one time before, and I assume I've never had a problem using the /dev/sdx designations because of that. I did just change boards recently and added the fifth drive, so maybe one or the other of those resulted in this occurring where it hadn't previously. Good to know that my installation isn't just flaky, and that this is easily resolved.

---

### Post by highgeere on 2009-02-07
I'm also thankful for your sig, drs305. I would have spent at least ten minutes trying to figure out how to thank you guys and mark the thread solved!

---

