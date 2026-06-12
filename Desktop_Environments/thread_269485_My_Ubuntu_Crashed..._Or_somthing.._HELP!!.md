---
title: "My Ubuntu Crashed... Or somthing.. HELP!!"
date: 2006-10-01
forum: Desktop Environments
---

### Post by ltr20 on 2006-10-01
Hey,

I'm running on a live CD now because I can't boot into my Ubuntu Install. I had ubuntu running for a month now and right before I rebooted I looked in the menu bar and saw that the icons had x's in front of the text and all the menus were missing!! The menu bar was broken..

I rebooted and found out that I couldn't boot into grub, i get a grub error.

How do i fix this??

---

### Post by ltr20 on 2006-10-01
bump

---

### Post by djrosen on 2006-10-01
> **ltr20 said:**
> 

{deteted}

I rebooted and found out that I couldn't boot into grub, i get a grub error.

How do i fix this??

Can you give a better description of the error?

---

### Post by ltr20 on 2006-10-02
i restored my windows MBR so i could boot into windows until i get this sorted out. I tried viewing my linux partition in Explore2FS and i don't see the partition anymore, i think it went kaput. 

How can i recover it?

---

### Post by Sef on 2006-10-02
Download and Burn [GParted]("http://gparted.sourceforge.net/livecd.php") to check and fix, if necessary, your partitions.

I believe that you can also use it to restore GRUB. If it doesn't, [click here.]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by ltr20 on 2006-10-02
it looks like my partition is damaged, how do i recover it?

---

### Post by ltr20 on 2006-10-02
anyone?

---

### Post by cptnapalm on 2006-10-02
one thing to do is to use cfdisk at a prompt.  Usage: cfdisk /dev/hda (or /dev/sda depending).  what does the partition setup look like there?

What kind of filesystem were you using?  (Just curious)

Can you mount read only?

here are some links:
[http://linux.omnipotent.net/article.php?article_id=12488](http://linux.omnipotent.net/article.php?article_id=12488)
[http://applications.linux.com/article.pl?sid=05/06/22/1941252&tid=129&tid=47](http://applications.linux.com/article.pl?sid=05/06/22/1941252&tid=129&tid=47)
[http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html](http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html)

Dont know if the above will help, but... maybe...

---

