---
title: "Doom 3 install issues"
date: 2010-05-02
forum: Gaming &amp; Leisure
---

### Post by Enlil on 2010-05-02
I'm trying to get Doom 3 to install on Ubuntu/Kubuntu 10.4 LTS. I had this same issue on 9.10, but after a few tries it worked, but now it won't. My issue is when I'm asked to copy over the .pk4 files from the cds, I put in the command, copy over the files. The only problem is that the file is not actually the full file it seems. It's the same size, everything. It even says pak000.pk4, etc. But it's not actually in .pk4 format. It's quite hard to explain, I'll try to attach an image which shows what I mean.

I've tried the command to move it over several times, and each time it just gives me that corrupted file. Any ideas?

---

### Post by glaze on 2010-05-03
> **Enlil said:**
> 
I've tried the command to move it over several times, and each time it just gives me that corrupted file. Any ideas?

Maybe your CD is damaged.

---

### Post by Enlil on 2010-05-03
That is a possibility. Though, it has worked in the past. In the screenshot provided, pak002.pk4 was from the first CD which by the way is extremely scratched. It didn't work the first time I used the command, but I tried it again, and sure enough it worked like is used to. I'm having issues with the 2nd, and 3rd CD which is a lot cleaner. Yet, no matter how many times I try, it still gives me that corrupted file.

---

### Post by ShadowTek on 2010-05-03
pk4 files are a type of archive. Can't you do an integrity test on them?

---

### Post by Xipher on 2010-05-03
They are actually zip compressed, you might try to install unzip and extract them.

---

### Post by ELD on 2010-05-04
Could be a corrupt cd, faulty cd drive (i had a similair problem with quake 4, my cd drive was dying).

---

### Post by Brebs on 2010-05-05
[ID's Doom 3 wiki page](http://zerowing.idsoftware.com/linux/doom/) provides md5sums of the .pk4 files, so check them against yours.

```
md5sum pak*.pk4
```

---

