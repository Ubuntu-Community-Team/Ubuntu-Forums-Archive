---
title: "New Dell Inspiron 6400 - did the live cd resize my disk?"
date: 2008-02-10
forum: Dell  Ubuntu Support
---

### Post by VazSingh on 2008-02-10
Hi there,
I bought a new dell inspiron last week which came with a 160GB hdd. From what I remmember 10GB were set aside for the 'recovery' partition (by dell).

Today I tried out live cd's of:
Ubuntu - 5.05
Kubuntu - 6.06 lts

After giving a little spin and not getting anywhere with Ubuntu (presumably because I have the old cd's), I flicked back to windows. In my computer I can see that the c:\ is not 136GB. Im sure it was a little more than that. 

There are no other partitions which I can see. Could the live cd have done something or is it paranoia?

kind regard,
Vaz

---

### Post by jimrz on 2008-02-10
The live cd will not touch your hdd, UNLESS you specifically told it to in G Parted or the installer's partitioner, and both give warnings that you are about to mess with your disk. More likely you are just seeing available drive space on your NOMINALLY 160 Gb hdd after the overhead of ntfs formatting and whatever hidden partitions (restore and probably a Dell utilities partition) you have are subtracted.

---

### Post by faulkes on 2008-02-10
> **VazSingh said:**
> Hi there,
I bought a new dell inspiron last week which came with a 160GB hdd. From what I remmember 10GB were set aside for the 'recovery' partition (by dell).

Today I tried out live cd's of:
Ubuntu - 5.05
Kubuntu - 6.06 lts

After giving a little spin and not getting anywhere with Ubuntu (presumably because I have the old cd's), I flicked back to windows. In my computer I can see that the c:\ is not 136GB. Im sure it was a little more than that. 

There are no other partitions which I can see. Could the live cd have done something or is it paranoia?

kind regard,
Vaz

Without more information, I can't say for sure, although it is unlikely that a live cd would repartition the drive without willfully and fully informing you.

You can fully check out what partitions exist within windows by going into the control panel (assuming XP), then:

Administrative Tools->Computer Management->Disk Management

That will list all partitions the system sees (as well as type and size).

Faulkes

---

### Post by VazSingh on 2008-02-12
Thank you I did not see any more partitions in disk partition so I'm guessing it's all in the mind. Thank you once again :)

---

