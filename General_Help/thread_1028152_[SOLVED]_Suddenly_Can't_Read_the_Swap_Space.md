---
title: "[SOLVED] Suddenly Can't Read the Swap Space"
date: 2009-01-02
forum: General Help
---

### Post by Cadeyrn on 2009-01-02
Simple problem: My computer is now way slower (irritating) because when I started it up, after loading Ubuntu, it showed the startup log thingy that's always shown, and I saw it saying that recognizing the swap space failed. I have yet to know whether this is a freak one-time-only glitch because I haven't had the chance to start my computer up again and won't for a while, but just in case, any help?

---

### Post by spcwingo on 2009-01-02
Try booting the live CD back up and using gparted to reformat the swap partition.

---

### Post by plucky on 2009-01-02
> **spcwingo said:**
> Try booting the live CD back up and using gparted to reformat the swap partition.

Why not do it from the live system,You just have to dismount the partition and use the partition editor.

Please post output from a terminal of ```
free -m
sudo fdisk -l
sudo blkid
cat /etc/fstab
```


Good Luck

---

### Post by Cadeyrn on 2009-01-02
Actually, I think I'd rather use the GParted iso because that way it's also easier to undo my mistake I made before: when I first installed Ubuntu, I made the space the size of my physical RAM, but now I know it's meant to be twice that.

---

### Post by Cadeyrn on 2009-01-02
Yeah, it was just a freak glitch. I forgot to watch the startup log but Ubuntu's Task Manager showed me a log of swap space use, and yes, it's totally being used now.

---

