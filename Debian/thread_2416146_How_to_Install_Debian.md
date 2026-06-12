---
title: "How to Install Debian"
date: 2019-04-05
forum: Debian
---

### Post by Shadius on 2019-04-05
Hi all,

I'm trying to install Debian on my laptop and it's just not installing.  Any installation option that I choose, nothing happens.  Can anyone help me?  I've never installed Debian before.  

Thanks in advance.

---

### Post by Rubi1200 on 2019-04-06
Hi,

Please post the boot info summary (see link in my signature) so we can get a better overview of what is going on.

Also, please post system specs. especially RAM, CPU, graphics card.

Thanks.

---

### Post by Shadius on 2019-04-08
> **Rubi1200 said:**
> Hi,

Please post the boot info summary (see link in my signature) so we can get a better overview of what is going on.

Also, please post system specs. especially RAM, CPU, graphics card.

Thanks.


Here you go:
[http://paste.ubuntu.com/p/48WTbsS9CW/](http://paste.ubuntu.com/p/48WTbsS9CW/)

It's an HP ProBook 640 G1

---

### Post by Rubi1200 on 2019-04-08
I'm concerned about this on /dev/sda > [COLOR=#000000]Invalid MBR Signature found[/COLOR]

What was on the drive before you wanted to install Debian?

---

### Post by Shadius on 2019-04-09
It was a Windows 7 PC, but I used DBAN on it to wipe it out.

---

### Post by Rubi1200 on 2019-04-09
I may be mistaken but I think you probably need to use something like GParted or a command line tool to create a partition table on the drive before you can install.

This article is slightly older but the information is pretty clear and even though i have not used Debian for a long time am pretty sure it contains fdisk and other tools you need:
[https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/](https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/)

Once you have the partitions set up you should be able to install.

---

### Post by Shadius on 2019-04-09
> **Rubi1200 said:**
> I may be mistaken but I think you probably need to use something like GParted or a command line tool to create a partition table on the drive before you can install.

This article is slightly older but the information is pretty clear and even though i have not used Debian for a long time am pretty sure it contains fdisk and other tools you need:
[https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/](https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/)

Once you have the partitions set up you should be able to install.

I find this strange because Ubuntu installed fine.  I don't understand why Debian wouldn't create its own partition table when installing.

---

### Post by Rubi1200 on 2019-04-09
Hmm, I also do not know why. Perhaps ask on the Debian forums for advice?

---

