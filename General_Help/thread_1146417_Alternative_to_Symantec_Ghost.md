---
title: "Alternative to Symantec Ghost?"
date: 2009-05-02
forum: General Help
---

### Post by Pnuts on 2009-05-02
Hello,

I've just recently gotten into Linux (month or 2 ago) and I am looking for a quick and easy method of making an image of my drive.

With Ghost I was able to get just the data, so instead of a 250gb image, it was a good 6gb or so. It was also fairly quick.

I found dd through searching around, however it grabs the whole drive and takes a considerable amount of time. I think in the end it was 22gb and took about 4 hours. With Ghost it was only about 20 minutes and about 6gb.

The catch, is if I restore the ghost, the drive wont boot. So, is there an alternative out there similar to ghost? Or is there a work around I could use? maybe seperate the /boot partition and only backup the data partition?

Thanks,
Pnuts

---

### Post by Paqman on 2009-05-02
[Partimage]("apt:partimage") does the exact same stuff as Ghost.

---

### Post by bardophile on 2009-05-02
You could try partimage (available from Synaptic Package Manager). I'm not sure if it's the exact tool used on[Clonezilla]("http://sourceforge.net/projects/clonezilla/"), but I've found Clonezilla to be extremely useful.

---

### Post by Pnuts on 2009-05-02
PartImage looks like it is exactly what im looking for. Thanks!

---

