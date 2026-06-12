---
title: "Swap"
date: 2009-01-05
forum: General Help
---

### Post by will2529 on 2009-01-05
hi I'm new to ubuntu and i need some help that i could not find on Google or here. i want to use my swap for world of warcraft and i really don't know how to do it. i have partition editor but i still don't know how to set it and i have yet to see a forum about it. i recently installed world of warcraft and i only have 470mb of ram and my game gets so lagged it crashes and i need to know how to solve that with swap. :)

---

### Post by blazemore on 2009-01-05
Well, you'd have to resize your partitions to make some space, then "format" the remaining space as swap.

Or use a swapfile:
Make the file:
```
sudo dd if=/dev/zero of=/swap bs=1024 count=524288
```

Make it into swap:
```
sudo mkswap /swap
```

Turn swap on:
```
sudo swapon /swap
```

Backup fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```

Make sure swap comes on every boot:
```
sudo echo /swap swap swap defaults 0 0 >> /etc/fstab
```

To verify if swap is activated, use
```
free -m
```

Edit: The word "swap" is starting to look very odd...

---

### Post by taurus on 2009-01-05
which new partition is your swap now?  Open a terminal and post the output of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
free -m
```

---

### Post by donkyhotay on 2009-01-05
As a clarification you do not put things on the 'swap'. The swap is a place for your system to use for virtual memory (like a windows page file). If you want to use that space for anything else you have to repartition as has been already mentioned.

---

### Post by blazemore on 2009-01-05
The benefit of my method is you can place the swap file anywhere, including on a USB flash drive.

---

### Post by will2529 on 2009-01-05
well now i know how to do that but now how do i use it for world of warcraft?

---

### Post by blazemore on 2009-01-06
It's done. Your system will use the swap when it gets low on RAM.

---

