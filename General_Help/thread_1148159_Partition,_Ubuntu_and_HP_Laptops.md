---
title: "Partition, Ubuntu and HP Laptops"
date: 2009-05-04
forum: General Help
---

### Post by rausuar on 2009-05-04
Hi all,

I use Ubuntu (Jaunty) in my laptop HP Pavilion dv2872, installed using WUBI.

However, I would like to install it in a different partition and completely apart from the other OS.

My question is how can I install Ubuntu without messing with th other partitions?, as you know, this laptops come with the partition of Windows, the recovery partition and a partition for diagnostics.  Is there any tutorial or document that explains how to do that?

Thanks!

---

### Post by KhaaL on 2009-05-04
Hi hausuar

I doubt there is a tutorial, besides the rule of thumb backup everything in case things go sour. Generally the installer does a good job preserving the other partitions, the only thing I've witnessed that might be messed up is the grub loader (which is easily fixed if you know how to).

So my advice is to use [clonezilla]("http://clonezilla.org/"), defrag your windows partitions and then install normally.

---

### Post by caljohnsmith on 2009-05-04
As KhaaL all ready pointed out, your best insurance against mistakes is to first back up everything. But to install Ubuntu without touching your other partitions, just select the "manual" partition option during the installation, and then you can select the partition you want to install Ubuntu to. If you need to modify or set up any partitions, I would recommend using Ubuntu's gparted partition editor (System > Admin > Partition Editor) to manually set up all your partitions before you go through the Ubuntu installer. Good luck and let us know how it goes or if you run into problems.

Cheers,
John

---

