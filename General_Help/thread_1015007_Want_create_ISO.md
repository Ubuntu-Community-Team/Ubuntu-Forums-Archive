---
title: "Want create ISO"
date: 2008-12-18
forum: General Help
---

### Post by curlynoodlekid on 2008-12-18
I have the ubuntu 8.10 intrepid ibex CD and i want make ISO file from that CD but the error  can read the CD using ultra iso so i checked it with nero toolkit cd speed and scan it and the error coz the folder of the CD is "POOL" folder is unreadable can some body help me upload that folder coz i cant download the full iso form ubuntu my connection slow....some body help me to upload that folder..

---

### Post by kanikilu on 2008-12-18
Are you sure that CD works? It sounds like maybe there's something wrong with it.

Maybe try creating it with another utility, such as InfraRecorder, ImgBurn, CDBurnerXP, etc...

---

### Post by andrew.46 on 2008-12-19
Hi,

Assuming your original CD of Intrepid Ibex is sound perhaps you could try to create *another* iso copy by placing your cd in the drive and running the following command:

```
cd Desktop
dd if=/dev/cdrom of=Intrepid_Ibex.iso bs=2048
```

And then burn this iso using Brasero, K3B or whatever your preferred application is. This method of creating iso's from Ubuntu cds has never failed me and I hope this will be the same for you :-).

All the best,

  Andrew

---

### Post by curlynoodlekid on 2008-12-20
I mean i dont have the ISO before only the Live CD Not the ISO contain on that cd so from live cd i want create the ISO file and installed run from the HD by using unetbootin tools

---

### Post by andrew.46 on 2008-12-20
Hi curlynoodlekid,

I will admit that I am still not entirely clear what you mean:

> **curlynoodlekid said:**
> I mean i dont have the ISO before only the Live CD Not the ISO contain on that cd so from live cd i want create the ISO file and installed run from the HD by using unetbootin tools

If you wish to create an iso file on your computer from a 'live' Ubuntu installation disc the command I gave you will do this. I have not used unebootin but I understand that it should be able to use such a file.

dd is of course a linux command. are you trying to do this from a windows partition?

All the best,

  Andrew

---

### Post by logos34 on 2008-12-20
I understood the OP to mean the 'pool' dir was corrupted...just needed that rather than download entire .iso (slow conection)

is this it

[http://archive.ubuntu.com/ubuntu/pool](http://archive.ubuntu.com/ubuntu/pool)

?

---

### Post by andrew.46 on 2008-12-20
Hi logos34,

> **logos34 said:**
> I understood the OP to mean the 'pool' dir was corrupted...just needed that rather than download entire .iso (slow conection)

I guess that makes more sense :-). I will admit though that if a single directory was corrupted on an installation cd I would tend to throw the cd in the bin as I would not trust it at all.

My advice would be, if this is the case to obtain another *full* copy. Hey curlynoodlekid if you are in Australia I will send you a copy myself for free.

Andrew

---

### Post by logos34 on 2008-12-20
> **andrew.46 said:**
> if a single directory was corrupted on an installation cd i would tend to throw the cd in the bin as i would not trust it at all.
+1

---

