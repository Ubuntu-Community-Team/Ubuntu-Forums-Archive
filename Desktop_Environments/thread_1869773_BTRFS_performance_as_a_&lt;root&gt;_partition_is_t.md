---
title: "BTRFS performance as a &lt;root&gt; partition is too slow"
date: 2011-10-26
forum: Desktop Environments
---

### Post by nicolasdiogo on 2011-10-26
hello,

i have installed ubuntu with BTRFS on my root partition as have found it to be so slow.  that i would like to find out if other have found the same.

in my case, any system upgrade has to be measured in 'ice ages' as they take so lonnnnng.

i have also found that it is possible to enable compression using btrfs *BUT* it seems that GRUB will not be able to read from the <root> partition if that is enabled!!

thus i will have to create a <boot> partition with ext3/4 to be able to improve performance using compression.

would it not be a *bug* with the installer to allow btrfs in <root> partition without having a <boot> partition ?

please post your comments and share your experience with BTRFS filesystem.


thanks,

Nicolas

---

### Post by prmcafee on 2011-10-26
This is probably not the answer you're looking for, but it's the only one I have.  BTRFS is still buggy.  I tried it once with installing 11.10 when 11.10 was in beta and I had all sorts of issues, one being that GRUB couldn't find a system image, and that it was horrifically slow booting.  The solution I have is to reinstall Ubuntu using EXT4 or something other than BTRFS, until they iron out all of the kinks.  EXT4 works for me the best.  It's fast and stable.

---

### Post by nicolasdiogo on 2011-10-27
thanks

i have considered to reinstall ubuntu.
but i though maibe i should give it a go and try improving things first.


maybe there is someone else who can offer an alternative to reinstall?

---

