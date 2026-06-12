---
title: "Backing Up Ubuntu Partition"
date: 2009-05-31
forum: General Help
---

### Post by Tanner2007 on 2009-05-31
Anyway to completely backup  my ubuntu partition to maybe an image I can save on my windows desktop?

I want to install another OS and have a tri boot, but lats time I tryed it jacked up my older ubuntu partition, making me not able to access it, even tho it showed up on grub boot loader, it load half way then froze and my keyboards light where flashing and was like that till I turn it off.

anyways I dotn want that to happen again so I wanna be able to backup my whole ubuntu partition, not personal data but everything, im new at linux and I worked hard on my ubuntu partition for days and Dont think id remember how  to do it again

so anyway guys?

---

### Post by mike555 on 2009-06-01
you could try "remastersys" , [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html) ....

---

### Post by binary10 on 2009-06-01
> **Tanner2007 said:**
> Anyway to completely backup  my ubuntu partition to maybe an image I can save on my windows desktop?

I want to install another OS and have a tri boot, but lats time I tryed it jacked up my older ubuntu partition, making me not able to access it, even tho it showed up on grub boot loader, it load half way then froze and my keyboards light where flashing and was like that till I turn it off.

anyways I dotn want that to happen again so I wanna be able to backup my whole ubuntu partition, not personal data but everything, im new at linux and I worked hard on my ubuntu partition for days and Dont think id remember how  to do it again

so anyway guys?

Did you miss out the word 'just' in the not <> personal data but everything ?

I'm an rsync junkie so would use various combos of rsync to keep a bloated backup copy to hand.

---

### Post by colau on 2009-06-01
> **mike555 said:**
> you could try "remastersys" , [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html) 
....
+1

---

### Post by VMC on 2009-06-01
You will get a lot of opinions regarding backups. I use two methods. [Clonezilla]("http://www.clonezilla.org/"), or [Parted Magic]("http://partedmagic.com/index.php")'s partimage.

You will end up with an image as you requested. If you have any questions as how to do this or how to restore, let me know. I've been using these methods for a long time with total success.

---

### Post by binary10 on 2009-06-01
clonezilla and others all good.. it just depends on what you want to do with the end data. Stuff it away in a draw or have bits of files available on demand maybe only to restore part of the data.

Clonezilla will create compressed datafiles for you, you can ssh serve them... but sometimes you can have these large files just hogging your disk and leave you wondering why you kept them.

---

