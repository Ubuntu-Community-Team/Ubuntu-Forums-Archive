---
title: "How do I add disk space to my Linux"
date: 2009-03-26
forum: General Help
---

### Post by koekjestrommel on 2009-03-26
I want to add 30 more Gigs to my linux, but how would I do that. Should I use puppy linux or anything else? Or will puppy fail?
[IMG]http://i273.photobucket.com/albums/jj202/k0ffiekopje/Untitled-1.jpg[/IMG]
pics say way more than words :)

Thanks ;)

---

### Post by Xero Xenith on 2009-03-26
The most reliable way is to get the GParted Live CD from [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") ([see here]("http://gparted.sourceforge.net/livecd.php") for more info), and use that to do the partitioning.

I'm guessing you'd want that 30GB to go to the root partition, not "NieuwVolume". So I'd move NieuwVolume to the far left, so there's lots of free space to its right. Then, you can extend the extended partition leftwards, and then you can add 30GB of space to the root partition (also leftwards) like that.

Note that in the GParted Live CD, the mountpoint fields will be blank, as they won't be mounted in the Live CD. They'll just be known as "sda1", "sda2" etc. This won't affect the final result in any way.

---

### Post by koekjestrommel on 2009-03-26
Should i also place linux to the left? And then add the unallocated space? Or doesnt that matter. Almost done placing XP to the left by the way. Hope it still works ;)

---

