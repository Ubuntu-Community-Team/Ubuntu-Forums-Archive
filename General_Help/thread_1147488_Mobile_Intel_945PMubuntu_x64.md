---
title: "Mobile Intel 945PM/ubuntu x64"
date: 2009-05-03
forum: General Help
---

### Post by Manac0re on 2009-05-03
Ok I have ubuntu 9.04 x64 running on my Dell M2010 the motherboard is Intel 945PM. 

ubuntu sees only 3.2 gig... I ve gone to the bios and there seems to be no memory mapping option.  Is my harware stopping ubuntu from using the full 4 gig and is there any work around?

oh and dont even get me started on my ati x1800 graphics card..... grrrrrr

---

### Post by gooligan on 2009-05-04
What do you mean by "ubuntu sees only 3.2 gig..."?
Could you post the output of "free -m"?

---

### Post by Manac0re on 2009-05-04
ok i did free - m and got:

             total       used       free     shared    buffers     cached
Mem:          3232       3106        125          0        793       1207
-/+ buffers/cache:       1105       2127
Swap:         7632          0       7632


i have 4 gig installed and 100% using unbuntu x64 any ideas???

thanking u kindly in advance

- Mana

---

### Post by gooligan on 2009-05-06
Could you provide the following outputs too?

```

$ uname -a
$ head /proc/meminfo

```

---

### Post by Manac0re on 2009-05-06
Sure thing ....

Linux manac0r-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

MemTotal:        3310112 kB
MemFree:         2284468 kB
Buffers:           35804 kB
Cached:           493944 kB
SwapCached:            0 kB
Active:           462824 kB
Inactive:         446272 kB
Active(anon):     386888 kB
Inactive(anon):        8 kB
Active(file):      75936 kB

As you can see only sees 3.3gig ram.  I ve checked my laptops bios and all memory feature are read only.  Any ideas??

Thank

-mana

---

### Post by gooligan on 2009-05-06
From what I can see, this does not seem like a Linux/Ubuntu issue [yet]
It appears that the BIOS is allowing the kernel to see only a about 3.2G of RAM
You can check the amount and kinds of RAM modules installed on your machine using the following command. Maybe that will help or provide a clue

```

$ sudo dmidecode -t memory

```

---

