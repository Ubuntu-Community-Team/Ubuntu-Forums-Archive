---
title: "Karmic: Stop kernel upgrades using pinning"
date: 2010-04-05
forum: Desktop Environments
---

### Post by aschlosberg on 2010-04-05
I installed Karmic for a friend (via Wubi as they still need Windows) but have had occasional problems after kernel upgrades. Until now I have been able to manually correct the issues but will no longer be able to so would like to lock the kernel at 2.6.31-17-generic as I am confident that this works.

I've researched pinning but am not 100% confident that I have this correct. I only have SSH access so using Synaptic is not an option.

If I create the file /etc/apt/preferences with the following will it be sufficient?

```
Package: linux-image-2.6.31-17-generic
Pin: release a=karmic
Pin-Priority: 1001
```I have noticed that there are multiple packages involved so am not sure if just doing this will be enough. Help would be greatly appreciated as I am very confident in Ubuntu but this in particular is a weak point.

---

### Post by falconindy on 2010-04-05
I'm not aware of the method you're using, but I used to use the below method for pinning packages (and I know it worked).

```
echo "packagename hold" | dpkg --set-selections
```

---

