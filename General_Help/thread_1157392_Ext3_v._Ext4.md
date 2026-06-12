---
title: "Ext3 v. Ext4"
date: 2009-05-12
forum: General Help
---

### Post by tanha on 2009-05-12
Does anyone else have similar performance hits on ext4 (sda3) relative to ext3 (sda1) with regard to disk read?

```
sudo hdparm -tT /dev/sda3

/dev/sda3:
 Timing cached reads:   3812 MB in  2.00 seconds = 1906.23 MB/sec
 Timing buffered disk reads:  162 MB in  3.03 seconds =  **53.52 MB/sec**

sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   3846 MB in  2.00 seconds = 1922.80 MB/sec
 Timing buffered disk reads:  314 MB in  3.01 seconds = **104.36 MB/sec**

```

---

### Post by lovinglinux on 2009-05-12
I don't think the performance hit is related to the file system format, but the partition position on the disk. Usually, partitions on the beginning of the disk are faster than partitions on the end of the disc, due to the radius size.

For example, I have two partitions on the same IDE disk. The first one (sda1) scores 59.82 Mb/s while the second (sda2) scores only 37.92 Mb/s. Both are ext4 and used to store personal data. The first one has 44% used space of 66 Gb, while the second has only 10% used space from 7.9 Gb. On the other hand, my first SATA partition (sdb2) scores 73.15 Mb/s while the second (sdb3) scores 70.76 Mb/s. The first one has 27% used space from 19 Gb and the second has 59% used space from 126 Gb.

As you can see, the partition with the worst result (sda2) has only 7.9 Gb, so the whole partition is next to the end of the disk. The sdb3 has not a huge performance difference from sdb2 because it is a huge partition and occupies most of the disc. I don't know if a SATA disk has a better performance regardless of the disc position, but it surely has a better performance when compared to IDE.

Your case is similar. Despite the fact that you are comparing different file systems, your ext4 partition (sda3) is certainly closer to the end of the disk than the ext3 partition (sda1).

---

### Post by tanha on 2009-05-12
> **lovinglinux said:**
> I don't think the performance hit is related to the file system format, but the partition position on the disk. Usually, partitions on the beginning of the disk are faster than partitions on the end of the disc, due to the radius size.

For example, I have two partitions on the same IDE disk. The first one (sda1) scores 59.82 Mb/s while the second (sda2) scores only 37.92 Mb/s. Both are ext4 and used to store personal data. The first one has 44% used space of 66 Gb, while the second has only 10% used space from 7.9 Gb. On the other hand, my first SATA partition (sdb2) scores 73.15 Mb/s while the second (sdb3) scores 70.76 Mb/s. The first one has 27% used space from 19 Gb and the second has 59% used space from 126 Gb.

As you can see, the partition with the worst result (sda2) has only 7.9 Gb, so the whole partition is next to the end of the disk. The sdb3 has not a huge performance difference from sdb2 because it is a huge partition and occupies most of the disc. I don't know if a SATA disk has a better performance regardless of the disc position, but it surely has a better performance when compared to IDE.

Your case is similar. Despite the fact that you are comparing different file systems, your ext4 partition (sda3) is certainly closer to the end of the disk than the ext3 partition (sda1).

Hmmm... I didn't think of that... The sda3 (ext4) partition is just 14 GB while the sda1 (ext3) is 430 GB.

---

### Post by bodhi.zazen on 2009-05-12
IMO claims that one file system is faster then another are over stated.

Sure if you create 10,000 1 kb files, move them, and then delete them you will see differences in the "benchmarks" , but such benchmarks are not exactly what most desktop users do most of the time.

IMO you should select a file system based on features not benchmarks.

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)
    [http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

    ext4 :
        [http://www.ibm.com/developerworks/linux/library/l-ext4/](http://www.ibm.com/developerworks/linux/library/l-ext4/)
        [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

---

### Post by lovinglinux on 2009-05-12
> **tanha said:**
> Hmmm... I didn't think of that... The sda3 (ext4) partition is just 14 GB while the sda1 (ext3) is 430 GB.

Yep. Your sda3 is similar to my sda2. They both have a small size compared to the size of the whole disk and are positioned on the end of it. That's explains the performance hit.

BTW, I had an overall performance boost on my machine when I formatted sda1 and sda2 as ext4. Before that, only sdb partitions where ext4.

---

