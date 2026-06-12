---
title: "Moving to a 1TB drive-- moving partitions"
date: 2009-02-04
forum: General Help
---

### Post by RevolutionMaster on 2009-02-04
I'm consolidating my five 120 GB drives into a single 1TB drive. As I have 3 OSs on here (WinXP, Win7,  & Ubuntu, I would like to just move my partitions from 1 drive to another. Is there a utility to move a partition to another drive. I could only use images if the program  images them regardless of filesystem.
Thanks for the help,
Nick

---

### Post by DGortze380 on 2009-02-05
> **RevolutionMaster said:**
> I'm consolidating my five 120 GB drives into a single 1TB drive. As I have 3 OSs on here (WinXP, Win7,  & Ubuntu, I would like to just move my partitions from 1 drive to another. Is there a utility to move a partition to another drive. I could only use images if the program  images them regardless of filesystem.
Thanks for the help,
Nick

Gparted will let you move partitions, it will take a LONG time, and you'll probably have to fix or reinstall GRUB.

---

### Post by RevolutionMaster on 2009-02-05
> **DGortze380 said:**
> Gparted will let you move partitions, it will take a LONG time, and you'll probably have to fix or reinstall GRUB. How do I move the partitions? When I say resize/move, it only lets me move it around on that drive.:???:

---

### Post by DGortze380 on 2009-02-05
> **RevolutionMaster said:**
> How do I move the partitions? When I say resize/move, it only lets me move it around on that drive.:???:

That's a good point, I honestly have never done it between two drives ... I assumed you could.

---

### Post by adult swim on 2009-02-05
you are going to have to set up your partitions on your tb drive and then just copy the respective partitions where you want them on the new drive.

---

### Post by RevolutionMaster on 2009-02-07
> **adult swim said:**
> you are going to have to set up your partitions on your tb drive and then just copy the respective partitions where you want them on the new drive.
Do you mean to copy the files?, and if so, how can I move the WinVista/7 bootloader over, just copy the MBR? Reinstalling 3 OSes is a pain, and I have programs that share OSs. (Steam is running from 1 location for XP/7.

---

### Post by dhughes on 2009-02-07
What's on each of those five hard drives, are the three operating systems on separate drives or all on one drive?

---

### Post by RevolutionMaster on 2009-02-07
> **dhughes said:**
> What's on each of those five hard drives, are the three operating systems on separate drives or all on one drive?
The OSes are on separate drives.
Drive 1: Windows XP + photos
Drive 2: Windows 7, 80 GB
Drive 3: Ubuntu, 120 GB
Drive 4: Video
Drive 5: Steam Games

---

### Post by -kg- on 2009-02-07
You cannot use GPartEd to move a partition from one physical drive to another...only on the same drive.  You also cannot move a partition from one location on the same drive to another location if there is another partition in the way, for instance, from the beginning of the drive to the end.  You would have to delete the first partition, move the first partition, then recreate the deleted partition after the move was complete.

In order to "move" a partition from one physical drive to another, you will need to create an image file of that partition, create a partition on the drive you wish to move it to, then recreate the files on that partition from the image.

Of course, when you're talking moving bootable partitions about, that means that your bootloader (GRUB in your case?) won't boot the partitions as before.  You will need to edit your GRUB menu.lst in order to boot them.

For further information on partitioning operations, see:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

