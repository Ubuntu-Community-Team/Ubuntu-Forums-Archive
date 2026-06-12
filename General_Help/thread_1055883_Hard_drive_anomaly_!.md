---
title: "Hard drive anomaly !"
date: 2009-01-31
forum: General Help
---

### Post by Bigneil on 2009-01-31
My ubuntu  HDD is 40GB but 'disk usage analyser' is convinced that the HDD is 53GB there is also an 80GB storage drive that, according to 'disk usage analyser' is 127GB. Does any body know why this would happen.?

The system is running well otherwise, with little or no glitches (just the odd compiz related freeze up)

---

### Post by Bigneil on 2009-01-31
oh, hang on a mo! i think it is seeing both drives as one?  the 80 is beeing seen as 74.5. and the 40 is beeing seen as 53.1 giving me a total of 127.6.

i still don't understand why the 40 gig drive is being recognised as 53.1????

---

### Post by Bigneil on 2009-01-31
any one have any thoughts on the subject.

P.S i have been reading the thread about defrag and anti virus on Ubuntu, and the comparison between linux and microsoft file systems. Very interesting;)

---

### Post by Tomatz on 2009-01-31
Is it possible that the drive has some partitioned space?

---

### Post by Bigneil on 2009-01-31
well, i know that the drive is 40GB, it says so on the top. but why 'disk usage analyser' thinks that total size is 53.1 is a mystery to me! 

It's not a problem as such, i just wondered if anybody else noticed simelar anomalies popping up? or, if any one had an explanation?

---

### Post by Tomatz on 2009-01-31
Probably has some unpartitioned space. Open a terminal and type:

```
sudo fdisk -l
```

Then post the output here.

---

### Post by Bigneil on 2009-01-31
ok i was wrong, the drive is not 40GB it is 30GB. but that still doesn't explain where the 53.1 comes from.

---

### Post by Bigneil on 2009-01-31
Oh! device sda2 extended. has it nicked a portion of my backup drive? and is seeing the parts as one drive that is 53.1 GB??

---

### Post by Tomatz on 2009-01-31
> **Bigneil said:**
> Oh! device sda2 extended. has it nicked a portion of my backup drive? and is seeing the parts as one drive that is 53.1 GB??

According to fdisk you have 2 drives. One at 30gb and one at 80gb?

---

### Post by Bigneil on 2009-01-31
Yes, a 30 and an 80. the 30 has my ubuntu, and the 80 is a storage volume.  

What i don't understand is that if the drive that has my ubuntu installed on it is 30 GB, how can my disk usage analiser tell me that i have a total file system capacity of 53.1?

I just don't understand unless, the analyser is seeing free space on the storage volume?  i don't want it to. it is unmounted when this result was shown. mounted it shows 127.6.

I just wanted to see how much free space was left on the 30 gig ubuntu volume.

---

### Post by Bigneil on 2009-01-31
here is the analyser with the back-up volume mounted

---

### Post by glotz on 2009-01-31
I don't see anything wrong with that picture.

---

### Post by Bigneil on 2009-01-31
I have to apologise. i have been an idiot. i had both boxes checked. i have 26.5 GB of my 30Gb, but it shows up twice because i have both boxes checked in the analyser.  Doh !!!

thank you for taking the time to try and help Tomatz :D


bigneil

---

### Post by Tomatz on 2009-01-31
> **Bigneil said:**
> I have to apologise. i have been an idiot. i had both boxes checked. i have 26.5 GB of my 30Gb, but it shows up twice because i have both boxes checked in the analyser.  Doh !!!

thank you for taking the time to try and help Tomatz :D


bigneil

No problem :lolflag: 

I have those days ](*,)

---

