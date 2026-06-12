---
title: "Grub Did Not Detect Dell Restore Partition (Ctrl F11 During Boot Up)"
date: 2011-02-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hayhursm on 2011-02-25
Hello,

I have a Dell XPS 400 and I installed Ubuntu 10.04 32-bit alongside the factory installed Dell Windows XP.  I made sure the Dell  Utility and Dell Restore Partitions were not touched during the  installation but now Ctrl F11 does not take me to the Restore program as  it previously did.  The GRUB Menu shows the Dell Utility Partition but  not the Dell Restore Partition. I ran "sudo update-grub" but that still  did not detect the Recovery Partition.  How can I fix this problem so  that Ctrl F11 will bring up the Dell Restore Application?   Any help  will always be greatly appreciated!!

---

### Post by gordintoronto on 2011-02-25
Can you run Accessories/Terminal, and enter this command:
sudo fdisk -l

---

### Post by hayhursm on 2011-02-25
> **gordintoronto said:**
> Can you run Accessories/Terminal, and enter this command:
sudo fdisk -l

I'm sorry but I can't.  I was doing this install for an out of town business and have since left.  Could you tell me what I'm looking for so when I go back in a few weeks I can remedy the problem?

---

### Post by gordintoronto on 2011-02-26
The command will show what partitions are actually on the hard drive.

---

### Post by hayhursm on 2011-02-26
> **gordintoronto said:**
> The command will show what partitions are actually on the hard drive.

Yes, I gathered that much but how do I get Grub to detect the Symantec Dell Restore Partition?  What does Grub look for to know that a partition can be booted to?

---

### Post by gordintoronto on 2011-02-28
> **hayhursm said:**
> Yes, I gathered that much but how do I get Grub to detect the Symantec Dell Restore Partition?  What does Grub look for to know that a partition can be booted to?

Sorry, I don't know the answer to that.

I have a working assumption that if you choose to boot Windows, that will give you a choice of Windows or the restore. Could be wrong.

---

### Post by hayhursm on 2011-03-02
> **gordintoronto said:**
> Sorry, I don't know the answer to that.

I have a working assumption that if you choose to boot Windows, that will give you a choice of Windows or the restore. Could be wrong.

I appreciate your input.  I will keep searching and maybe I will get lucky and someone has experienced this problem already.

---

