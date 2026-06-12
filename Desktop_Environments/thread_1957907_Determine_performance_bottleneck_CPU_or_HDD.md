---
title: "Determine performance bottleneck: CPU or HDD"
date: 2012-04-13
forum: Desktop Environments
---

### Post by Skyo on 2012-04-13
Dear ubuntu forum,




I wrote a script which unzips a large amount of zipfiles and parses the containing txt-files.
This whole script need aprox. 2 hours and I would like to check, whether I can boost it up a little.
[U][I]
Therefore I ask myself, what the performance bottleneck of my operations (especially 'unzip'!) is, CPU or HDD?[/I][/U]

If the CPU limits, more precisly one of its cores, I would start to thread my script.
If the HDD limits, no adjustments can be done (as long as I do not want to buy a faster SDD)


I need some kind of HDD + CPU benchmark. As far as I know, some hdd benchmark tools test compression performance.
Which tools / test setup can be used to answer my questions?



I appreciate your help, thank you very much, skyo.

---

### Post by 3Miro on 2012-04-13
If you have a lot of RAM, you can try to unzip the files in ramdisk. If you are creating and deleting lots of small files, ramdisk should speedup things tremendously. If not, then the CPU is the bottleneck.

[http://www.ubuntuka.com/ubuntu-ramdisk-ramdrive-easy-way/](http://www.ubuntuka.com/ubuntu-ramdisk-ramdrive-easy-way/)

---

### Post by Skyo on 2012-04-14
Is there a way to determine,  how large an unzipped archive will be, without actually unziping it? If so, I could unzip 4GB-- archives into RAM and 4GB++ onto the slower HD. Edit: Will test your suggestion as soon as I can.

---

### Post by 3Miro on 2012-04-14
> **Skyo said:**
> Is there a way to determine,  how large an unzipped archive will be, without actually unziping it? If so, I could unzip 4GB-- archives into RAM and 4GB++ onto the slower HD. Edit: Will test your suggestion as soon as I can.

I remember RAR keeping statistics about the compression ration, then you can use that to determine the size of the decompressed file. I don't know if zip does that or not.

---

### Post by Gyokuro on 2012-04-14
> **3Miro said:**
> I remember RAR keeping statistics about the compression ration, then you can use that to determine the size of the decompressed file. I don't know if zip does that or not.

zipinfo archive.zip should show you the relevant information

---

