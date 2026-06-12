---
title: "Disk defrag app for Ubuntu?"
date: 2009-06-03
forum: General Help
---

### Post by Cityscape on 2009-06-03
Where can i get a free defrag program for Ubuntu?
Do any have scheduled defrag?
Which will work fastest on slower hardware (667 MHz CPU) ?

Thanks for any help :KS

---

### Post by k420 on 2009-06-03
Read this article [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by michy99 on 2009-06-03
Linux file systems have very little fragmentation, so it is usually not a problem.

---

### Post by salvachn on 2009-06-03
Try
```

fsck -f

```This will show you the amount of fragmentation. If the output says less than 10% of your files are non-contiguous you need not defrag. I know of a utility called defrag, but am not sure if it works in ext3.

---

### Post by k420 on 2009-06-03
> **salvachn said:**
> Try
```

fsck -f

```This will show you the amount of fragmentation. If the output says less than 10% of your files are non-contiguous you need not defrag. I know of a utility called defrag, but am not sure if it works in ext3.

This causes sever dmagae if run while mounted

---

### Post by salvachn on 2009-06-03
@ k420
That was a pretty insightful article! Thanks.

---

### Post by prvteprts on 2009-06-05
I know there really isn't a need to defrag a Linux filesystem. But here's my question: Is there an app for Ubuntu/Linux to defrag FAT and/or NTFS? 

Why would we need this? Well it may be the case that most of us have partitions other than / and swap, which we use to store files that other OSes can read. Also if you dualboot with a legacy Windoze installation, it would sometimes be useful to be able to defrag C: from Ubuntu. Like in my case, I don't really like booting into XP anymore, but I still keep it (legacy install) in case someone else needs to use my computer or just to check if new hardware are functioning when I can't get them to run in Ubuntu.

Perhaps the same could be said about virus scanners. Yes, at this point there is no real virus threat for Linux users. But I have installed antivirus software on Ubuntu so that 1) I could clean Windoze-based partitions from viruses, and 2) I could prevent spreading viruses to my friends or family who use Windoze.

---

### Post by logos34 on 2009-06-05
> **prvteprts said:**
> Like in my case, I don't really like booting into XP anymore, but I still keep it (legacy install) in case someone else needs to use my computer or just to check if new hardware are functioning when I can't get them to run in Ubuntu.

yeah, I've always wondered why there's no defrag tool in ntfsprogs tools suite...lots of people have ntfs data partitions they access from linux while hardly running doze anymore

---

### Post by TrakerJon on 2009-06-10
Defrag (or fidefrag I should say)

sudo apt-get install bzr python-psyco
bzr branch lp:fidefrag
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>


Don't defrag /sys (you won't like the result) I usually just defrag /usr /home /var /lib and /etc

---

### Post by hal8000 on 2009-06-10
Con Kolivas wrote a defrag script:

[http://ck.kolivas.org/apps/defrag/defrag-0.06/defrag](http://ck.kolivas.org/apps/defrag/defrag-0.06/defrag)

After 5 years of use my old Suse /home partition had just a mere 0.5% fragmentation! Filesystem was ext2

---

### Post by hal8000 on 2009-06-10
> **prvteprts said:**
> I know there really isn't a need to defrag a Linux filesystem. But here's my question: Is there an app for Ubuntu/Linux to defrag FAT and/or NTFS? 



There was an article about this in Linux magazine.

It stated that when Ntfsprogs was wrote, there was not a lot of interest at that time for defragging NTFS file systems from linux.
Opinion may have changed now.

---

### Post by prvteprts on 2009-06-11
Thanks, I'll check it out. It seems to have a defrag option.

---

### Post by emeraldgirl08 on 2009-06-11
Sorry, but since we're talking about Windoze system tools- How about the Scandisk. I know that once in a while Ubuntu will do it on startup. How do I determine when the next scheduled one is and is there a way to initiate it via terminal?

---

### Post by prvteprts on 2009-06-11
> **emeraldgirl08 said:**
> Sorry, but since we're talking about Windoze system tools- How about the Scandisk. I know that once in a while Ubuntu will do it on startup. How do I determine when the next scheduled one is and is there a way to initiate it via terminal?

"Scandisk" in our world would be fsck. It seems that Ubuntu will force disk checking after every 26 times the main partition is mounted. To initiate it in terminal, just type sudo fsck. However, I wouldn't suggest that because in order to proceed with that you would need to force a dismount. Just fsck from safe mode instead.

---

