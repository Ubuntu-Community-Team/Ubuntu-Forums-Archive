---
title: "Disk partition"
date: 2009-02-03
forum: General Help
---

### Post by draxz on 2009-02-03
I have just installed Ubuntu by creating a separate partition (I reinstalled XP and backed up my data to a external hard drive).

I let Ubuntu decide how much to partition. I have a 60GB, 1 GB RAM XP. Ubuntu now has 46GB and 7GB free space for windows. 

I am going to use Ubundu primarily but still want to keep XP to run windows only programs.

Do you guys think 7Gb is enough for XP ( I have no files on it, just system files) since I wont be using XP and if I do have to re-partition can I do it with out reinstalling

---

### Post by dayanandasaraswati on 2009-02-03
I think 7GB will be enough for Windows if you're not going to install big softwares in it. If you still want some more space, you can use gparted to partition your 46GB Linux partition and create another ntfs partition which Windows can use it. But you cant add it with the existing 7GB partition without reinstalling XP.

---

### Post by draxz on 2009-02-03
Hello,

If I do have to install software's it will be MSN and yahoo for voice and video chat. Is gparted already in Ubuntu or do I have to download. If I re-partition will I have to  boot from the linux cd and select the space (will this delete my files on linux) and how do I back up my linux files

I am also from chennai but moved to toronto

---

### Post by dayanandasaraswati on 2009-02-03
Great to see a person from Chennai in the Ubuntu community!! If a lot of space is left on your Ubuntu partition, you need not backup any data if you are not going to slice of a lot of space.

---

### Post by howefield on 2009-02-03
> **shipshape said:**
> You can only create another partition in Ubunto installed partition by using gparted. For that you have to install gparted. Prerequisites are to add universe and multiverse repositories. Then in a terminal window type:
sudo apt-get install gparted

No, he won't be able to use gparted in the way you suggest, it will need the live cd so the Ubuntu (note the spelling) partition will not be mounted.

---

### Post by zvacet on 2009-02-03
@ **draxz**

If you want to make your Windows partition bigger then download [Gparted live CD]("http://gparted.sourceforge.net/") and with it shrink your Ubuntu partition and add unallocaed space to your Windows partition.

---

### Post by draxz on 2009-02-03
So I download Gparted and I can re-partition it and it wont change or delete any files on Ubuntu. 

If it does not work how can I remove Ubuntu and reinstall it and partition it again?

Thanks guys

---

### Post by draxz on 2009-02-03
> **dayanandasaraswati said:**
> Great to see a person from Chennai in the Ubuntu community!! If a lot of space is left on your Ubuntu partition, you need not backup any data if you are not going to slice of a lot of space.


hello,

So where are you in chennai, I used to live in Egmore. 
I was there in the summer. What do you do?

---

### Post by draxz on 2009-02-03
another question

Can I switch between OS with out restarting

---

### Post by howefield on 2009-02-03
Not on a dual boot system, you would need to reboot each time you wanted to use the other OS.

One way round that would be to use a virtual machine, you could have multiple OS running simultaneously.

---

