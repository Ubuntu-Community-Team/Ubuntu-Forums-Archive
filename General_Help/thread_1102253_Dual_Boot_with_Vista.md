---
title: "Dual Boot with Vista"
date: 2009-03-21
forum: General Help
---

### Post by timjm25 on 2009-03-21
Hi Again:

I created a dual boot with Vista, and with Ubuntu being the first installed OS.

I was wondering if there is a way to resize the Ubuntu partition and then to reallocate the freed up space to Vista without having to reformat any of the partitions.

Thanks.

---

### Post by Twitch6000 on 2009-03-21
> **timjm25 said:**
> Hi Again:

I created a dual boot with Vista, and with Ubuntu being the first installed OS.

I was wondering if there is a way to resize the Ubuntu partition and then to reallocate the freed up space to Vista without having to reformat any of the partitions.

Thanks.

Yes there should be a way,either with the inbuilt Vista partitioning tool or Ubuntu partitioning tool.

---

### Post by lunatico on 2009-03-21
> **timjm25 said:**
> I was wondering if there is a way to resize the Ubuntu partition and then to reallocate the freed up space to Vista without having to reformat any of the partitions.

I would recommend booting into a [GParted]("http://gparted.sourceforge.net/") Live CD.

---

### Post by timjm25 on 2009-03-22
Gparted Live CD worked to resize the partitions.

The problem now is that I cannot log into Vista - there is an error.

Do I have to go in a fix something in the GRUB menu list file?

Thanks.

---

### Post by lunatico on 2009-03-23
> **timjm25 said:**
> Gparted Live CD worked to resize the partitions.

The problem now is that I cannot log into Vista - there is an error.

Do I have to go in a fix something in the GRUB menu list file?

Thanks.

What error? The only error I would expect is a windows check disk run because the size changed.
I don't think you should have to change anything in GRUB menu list, you only resized right? You didn't deleted or created new partitions?

---

### Post by revelationman on 2009-03-23
Well it sounds like you have to repair Vista best way to do that is get your Vista DVD and boot into it and do the repair. Vista might repair the partition tables however with that being said I am not sure what will happen to you Ubuntu partition.

---

### Post by lunatico on 2009-03-23
> **revelationman said:**
> Well it sounds like you have to repair Vista best way to do that is get your Vista DVD and boot into it and do the repair. Vista might repair the partition tables however with that being said I am not sure what will happen to you Ubuntu partition.

Well if that's the case and Vista rebuilds its own MBR then from Vista you can configure a dual boot menu. There are loads of tutorials online on how to do this. So you will not use GRUB anymore. But I'm still intrigued of what happened, resizing the partitions shouldn't mess things up like this.

---

