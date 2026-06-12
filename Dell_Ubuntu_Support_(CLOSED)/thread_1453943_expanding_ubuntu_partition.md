---
title: "expanding ubuntu partition"
date: 2010-04-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abooks on 2010-04-13
I'm trying to expand ubuntu partition on a mini 10, trying to load bootable gparted  and failing miserably. Do I really need to do this, or now that I've shrunk 7 can I just reload (or upgrade?) 9.04? A little help for this frustrated n00b, please. Or failing that, tell me where I can ask questions like this.

---

### Post by Sentinel83 on 2010-04-14
Hi abooks,

Do you have a ubuntu LiveCD around?  If you boot to the LiveCD, then type 

```
sudo gparted
```

it should launch gparted and give you the ability to resize the partitions on the machine.  Once it is complete, restart.

Have you tried this already?

---

### Post by abooks on 2010-04-14
I haven't yet, but I will when I get home. Since it's a netbook, will I be able to boot from a live CD in an external drive, or will I have to download a bootable version? Or do I have to use unetbootin to make a bootable CD or thumb drive? (I hope not)

---

### Post by C.S.Cameron on 2010-04-14
A bootable pendrive would work nicely but you should be able to get your BIOS to boot from an external optical drive.
I'm not sure what key you press on a mini 10 for boot options?

---

### Post by abooks on 2010-04-14
OK, so the old 9.04 stick worked, and I reinstalled it, I thought, in the unallocated space I made by shrinking 7. But it STILL tells me there's no room to download updates. sda2 (7) has 88GB, sda4 (ubuntu) has 56 GB, sda7 (which I guess is the root one)has 2.33 GB and is almost full. I've cleaned and tried to spiff it, but apparently it's just not big enough. I do have a little unallocated space, and, I guess because I reinstalled 9.04, two swap partitions with 172 MB. I can't figure out how to zap one of swaps and use the space to expand sda 7. Any ideas?

---

