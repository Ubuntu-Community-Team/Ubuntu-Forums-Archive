---
title: "Kill Disk"
date: 2008-12-23
forum: General Help
---

### Post by Wickd on 2008-12-23
Hi there

I need a open source alternative to use to completely kill a disk.

I already have a DRBL server set up so I would like to get something that I could incorporate with that. But either way, as long as it is opensource.

Coolio ;)

---

### Post by Titan8990 on 2008-12-23
You can use nearly any Live linux cd with the dd command. The ubuntu cd will work.

You should note that this will take quite a long time:


dd if=/dev/zero of=/dev/DRIVENAME


The above command will write all 0s to the device you specify in of= 


Use with caution.

---

### Post by dagnabit dang doohickey on 2008-12-23
[DBAN]("http://www.dban.org/")

---

### Post by hyper_ch on 2008-12-23
either DD or DBAN :)

---

