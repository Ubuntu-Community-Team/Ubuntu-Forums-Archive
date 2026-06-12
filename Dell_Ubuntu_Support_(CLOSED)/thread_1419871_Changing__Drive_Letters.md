---
title: "Changing  Drive Letters"
date: 2010-03-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by daveritah on 2010-03-02
I have a Dell Inspiron 1501 with AMD 64 processor. When loading Ubuntu, I made a mistake and removed my XP operating system. I used an old XP disk and reloaded XP, however when it formatted and reloaded XP, it placed it in my E:/ instead of my C:/. I went to microsoft and followed the procedure to change my drive letter. However, when I came to box that would allow me to change my drive letter, it would not allow me to check that box and change my drive letter from E:/ back to C:/. How can I change my drive letter for my XP, presently, it will not allow me to load any programs from my disk. Second question, If I change my drive letter, will grub recognize my new drive letter?

---

### Post by isaacobezo on 2010-03-02
I am pretty sure that Windows will look at the Physical partitions and assign Letter values to them. As I recall, if you had two windows partitions, each windows installation would be assigned letter values for their drives depending on their location on the partition table.

I would just wipe it, install windows first then Ubuntu. Because an E:\Windows path would make me go insane. There probably is a better way of handling this, though.

---

### Post by daveritah on 2010-03-07
This was solved by repartitioning the hard drive and reload the OS's.

---

### Post by mikewhatever on 2010-03-08
All of that just to change drive letter?! Well great, now all malware programmed to look for C:\Windows... will be more then ready to infect you.

---

