---
title: "Multiple swap partitions?"
date: 2008-12-20
forum: General Help
---

### Post by Dannik on 2008-12-20
So I was just playing around with command prompt. I checked partitions installed on my hard drive and noticed that Ubuntu shows my swap partition to be 2 partitions in 1. Is that a mistake?

I've attached a screenshot of fdisk's output.

---

### Post by david_lynch on 2008-12-20
> **Dannik said:**
> So I was just playing around with command prompt. I checked partitions installed on my hard drive and noticed that Ubuntu shows my swap partition to be 2 partitions in 1. Is that a mistake?

I've attached a screenshot of fdisk's output.

I see only a single swap partition. You have an extended partition (sda3) which contains the logical partition (sda5) where your swap resides.

---

### Post by Dannik on 2008-12-20
Oh, I see. I saw 2 partitions, having same Start/End block values and assumed it's 2 same partitions. Thanks a lot for clearing this out for me.

---

### Post by jerome1232 on 2008-12-20
> **Dannik said:**
> So I was just playing around with command prompt. I checked partitions installed on my hard drive and noticed that Ubuntu shows my swap partition to be 2 partitions in 1. Is that a mistake?

I've attached a screenshot of fdisk's output.

Technically a logical partition is a partition inside a partition.

A hard disk can have up to 4 physical partitions. To be able to put more than 4 partitions on one disk they came up with logical partitions, you create a physical partition (called an extended partition) and it can contain up to 15 logical partitions within itself. Which raises the maximum to 60 partitions on one disk.

---

### Post by networm1230 on 2008-12-20
hello! I do not know much about partitions but I know of a tool to wipe your hard drive or one or more partitions on a drive  [http://www.dban.org/](http://www.dban.org/)

hop this helps you

---

