---
title: "raid no longer loading on boot?"
date: 2009-04-15
forum: General Help
---

### Post by IndieRockSteve on 2009-04-15
recently my Mythbuntu install running 2.6.27-11-generic stopped loading the RAID modules and assembling my array on booting.  once booted and I do a manual
modprove raid456
mdadm --assemble --scan

the array loads fine with no errors so it doesn't look like anything is wrong with the array.

I'm also not seeing any errors in any of the logs.

anyone have any idea what's going on or possible ideas on how to fix it?

thanks!

---

### Post by fjgaude on 2009-04-16
What does your /etc/fstab file look like?

---

### Post by Nohthee8 on 2009-04-16
I seem to have a similar problem on Intrepid.

Except that I haven't yet been able to manually re-assemble the problem array.

```

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdb4[0](S) sdf4[4](S) sde4[3](S) sdd4[2](S) sdc4[1](S)
      4829419520 blocks

md0 : active raid1 sdb2[0] sdf2[2](S) sdc2[1]
      9767424 blocks [2/2] [UU]

unused devices: <none>

```


Could be related to this kernel bug:

  [http://bugzilla.kernel.org/show_bug.cgi?id=11967](http://bugzilla.kernel.org/show_bug.cgi?id=11967)

> 
  "When disks are removed from a raid10 set, then readded,
  the raid10 driver marks the disks as spare and doesn't resync."


I could do with some advice on how to further diagnose the problem, and on how to work around it, e.g. how to re-assemble the problem array manually.

---

