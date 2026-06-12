---
title: "Grow/Expand RAID 0 Array"
date: 2009-06-11
forum: General Help
---

### Post by Ocxic on 2009-06-11
I currently have a 1TB Raid0 array setup(2x500GB) and I need to add another 500GB drive to the mix to bring the total to 1.5TB(3x500GB).
The only problem is i can't find out how to grow the RAID0 array the man pages for mdadm says the Grow option only works with RAID 1/4/5/6.

Does anyone know a way I can expand my array to included the new drive??

---

### Post by nandemonai on 2009-06-11
> **Ocxic said:**
> I currently have a 1TB Raid0 array setup(2x500GB) and I need to add another 500GB drive to the mix to bring the total to 1.5TB(3x500GB).
The only problem is i can't find out how to grow the RAID0 array the man pages for mdadm says the Grow option only works with RAID 1/4/5/6.

Does anyone know a way I can expand my array to included the new drive??

I've never seen the ability to 'extend' RAID 0. I'm pretty sure it just cant be done because it stripes all data across each disk in the array. 

Best bet is to re-create the RAID array and restore from a backup.

---

### Post by jerrrys on 2009-06-11
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by Ocxic on 2009-06-11
I don't have the ability to backup the data, and re-create the array. And the wiki article does not have the info I'm looking for.

---

### Post by nandemonai on 2009-06-11
> **Ocxic said:**
> I don't have the ability to backup the data, and re-create the array. And the wiki article does not have the info I'm looking for.

Ouch, RAID 0 and you have no backups? You're a brave person. One disk goes and so does the whole array.

---

### Post by surfed on 2009-06-11
> **Ocxic said:**
> I currently have a 1TB Raid0 array setup(2x500GB) and I need to add another 500GB drive to the mix to bring the total to 1.5TB(3x500GB).
The only problem is i can't find out how to grow the RAID0 array the man pages for mdadm says the Grow option only works with RAID 1/4/5/6.

Does anyone know a way I can expand my array to included the new drive??


You are out of luck my friend.

---

### Post by fjgaude on 2009-06-11
Use your backup copy of what's on the raid0 array. Then create a three-drive array. You do have a backup, eh?

---

