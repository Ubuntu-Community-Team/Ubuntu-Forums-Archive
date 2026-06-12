---
title: "FAT32 Partion Label ~ (SDA 5)"
date: 2009-06-10
forum: General Help
---

### Post by Imbuntu on 2009-06-10
Hi Everyone,

I've been using Ubuntu since about December 2008 (version 9.4 now) and have found it very time consuming to get to grips with (but doesn't crash like windows) - anyhow one recent problem I have at the moment is when I open Nautilus (file browser) the label to my FAT32 (my data) partition changed from "DATA" to  "?PNG" and a strange dice4 symbol at the end of it.  I checked the FSTAB file and that appears in order:-

UUID=49BE-CD33	/media/DATA	vfat	defaults	0

Is there something wrong with this line (it was working OK) - also checking with Mount manager 0.2.6 on info on /dev/sda5 reports "Product" with the same crazy name - however when I point to /media/DATA in the file manager the directory is fine (also OK when pointing to the crazy name)

Any ideas appreciated.  I've un-installed windows so can't use scandisk or check the label with windows. (Also nothing appears wrong with the linux partitions).

---

### Post by reeseslover531 on 2009-06-10
I doubt this is it, but there should be two 0s at the end as in 
```
 UUID=49BE-CD33 /media/DATA vfat defaults 0 0 
``` notice the last 0.

---

### Post by Imbuntu on 2009-06-11
> **reeseslover531 said:**
> I doubt this is it, but there should be two 0s at the end as in 
```
 UUID=49BE-CD33 /media/DATA vfat defaults 0 0 
``` notice the last 0.

This was a typo - sorry - thanks anyway for pointing it out - any other people out there with any ideas what could be wrong?

Additional note:-  In Gparted it appears to be the label that's wrong - can I change the label without re-formatting - if so a step by step would help.  Thanks.

---

### Post by drs305 on 2009-06-11
> **Imbuntu said:**
> 
Any ideas appreciated.  I've un-installed windows so can't use scandisk or check the label with windows. (Also nothing appears wrong with the linux partitions).

You can check the label *and *UUID with:
```

sudo blkid -c /dev/null

```

If the label isn't correct, recent versions of *gparted* provide the ability to label it from within the program.

---

### Post by Imbuntu on 2009-06-12
> **drs305 said:**
> You can check the label *and *UUID with:
```

sudo blkid -c /dev/null

```

If the label isn't correct, recent versions of *gparted* provide the ability to label it from within the program.

The problem was that the partition had been corrupted - so I re-formatted it with Gparted and all is well now - fortunately I had a backup of all my files.

Thanks for all your help.

---

