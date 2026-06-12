---
title: "Partition Requirement For Installing windows XP on vmware"
date: 2008-02-04
forum: Desktop Environments
---

### Post by mohtasham1983 on 2008-02-04
Hi,

I have a laptop with 40GB hard drive. I have specified 14GB for windows XP, 12GB for the linux file system and the rest for my home directory. 

I'm developing a web application so I need to test everything on IE as well, so I decided to install XP on vmware, however, I don't have enough space on my ext3 partitions. 

I read somewhere that it's a better idea to install vmware and then install win xp on it. So I want to format the entire windows partition and convert it to ext3. 

I'm wondering if I do that, can I use the new formatted partition as my windows partition or I have to use linux file system space for installing xp?

I have never worked with vmware and don't know exactly what are the requirements.

I really appreciate your help.

Thanks in advance.

---

### Post by pieisgood4589 on 2008-02-04
Why not install Windows directly from the disk? Just specify the empty partition!

---

### Post by mohtasham1983 on 2008-02-04
I already have windows installed. I need to test the website I'm developing on IE. Currently, my website is located on my ubuntu machine. If I switch back to windows, I don't have the website up and running anymore.

---

### Post by VMan on 2008-02-07
Not sure if this will answer your question or not. . .but

I have VMware player installed and have three separate virtual Windows XP installations (needed for various reasons).  The smallest Windows XP installation takes up about 5 gigs.  The largest takes up about 9 gig.  I have the virtual machines' hard drives set to grow as needed up to a maximum of 20 gigs.  I also have a virtual Windows Vista, but it runs so slow and bogs the whole machine down so much it is almost unusable.  I've been playing with VMware quite a bit lately.  I'm not an expert by any means, but feel free to ask me for help.  Post here and send a PM (I don't check the forums every day and the new post may get buried before I get back).

---

### Post by mohtasham1983 on 2008-02-07
Thanks man.

I just formatted my NTFS partition then installed win xp virtual machine in that partition. I just wasn't sure if vmware gives any option for selecting the partition.

---

