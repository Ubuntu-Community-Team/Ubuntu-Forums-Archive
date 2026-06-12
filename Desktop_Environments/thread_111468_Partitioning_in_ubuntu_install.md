---
title: "Partitioning in ubuntu install"
date: 2006-01-02
forum: Desktop Environments
---

### Post by Doc504 on 2006-01-02
I'm using the ubuntu 5.10 cd and trying to install on my old win98/2nd.  I understand that both os's can operate together.:confused:  Correct?
When I get to the partition part of the install, I'm confused as to what to click on:confused: 
The "help option on parititioning" does NOT:mad:  help me.
What partitioning step should I use in order to run both os's on my pc?
Thanks!

---

### Post by az on 2006-01-02
Yes, a lot of people dual-boot like that.

The default behaviour is to offer to shrink the size of an existing partition to make room for another one.  In that case, you are asked what size to make the new partition.

If you want to do more intricate manipulations of your partitions, you can use manual partitioning.

It if only offers to delete an existing partitoin, you may have a wonky partition table - usually, people who have user some third-party partitioning software experience this.  The ubuntu installer partitioner is very conservative and if it cannot safely resize your partition, it will not offer you the opportunity to do so.

---

### Post by toc on 2006-01-02
I do this: 
 I make linux /ext3/ and swap partition with third-party software in Windows and than start instalation of Ubuntu. In that way you don`t need to repartition your harddisk again and everything is ready for instalation - just skip partitioning in instalation process.

---

### Post by Zalbor on 2006-01-02
Also, if you're going to be resizing a windows partition, make sure to have a defrag first, just to be sure. Also a backup wouldn't be a bad idea.

---

