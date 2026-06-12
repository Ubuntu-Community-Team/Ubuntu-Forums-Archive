---
title: "Ubuntu Sees Vista, but vista dosnt see Ubuntu?"
date: 2009-05-23
forum: General Help
---

### Post by Penguinish on 2009-05-23
When im on ubuntu, i have access to my vista partition, and can access files from it and what not, but when im on Vista, i can not see my ubuntu partition to acess files.

How would i go about making it where both partions can accessed from either os.

---

### Post by mcduck on 2009-05-23
That is quite normal, Microsoft has decided to only support it's own file systems so windows isn't able to read anything else.

But there are some 3rd party drivers for other file systems available, for Ext2/Ext3 support I recommend this one: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by Penguinish on 2009-05-23
> **mcduck said:**
> That is quite normal, Microsoft has decided to only support it's own file systems so windows isn't able to read anything else.

But there are some 3rd party drivers for other file systems available, for Ext2/Ext3 support I recommend this one: [http://www.fs-driver.org/](http://www.fs-driver.org/)


Thanks, next time i boot up windows (which is not soon I hope) ill download that and try it out.

---

### Post by DeMus on 2009-05-23
> **mcduck said:**
> That is quite normal, Microsoft has decided to only support it's own file systems so windows isn't able to read anything else.

But there are some 3rd party drivers for other file systems available, for Ext2/Ext3 support I recommend this one: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

Right. It's the arrogance of Microsoft. Outside their Windows there is nothing.
Well, we know better.

---

### Post by mirons on 2009-05-23
IMHO it's worth considering a separate partition for data formatted with fat32 or NTFS. This would prevent FS corruption from buggy drivers, upgrade to ext4 without compatibility problem and avoid messing up OS related files from another (the general priciple is: if they can't see each other they can't harm each other). The disadvantage is you have to decide about how much space give for data and for apps in both system. It depends on the need and on the taste, I'm not suggesting to do so, just consider.

---

### Post by VCoolio on 2009-05-23
Be careful when you install that patch in windows. A friend of mine did that and Windows said: new partition found; do you want to format? You don't want that. Besides that it works.

---

### Post by ceciliaFX on 2009-05-23
> **mirons said:**
> IMHO it's worth considering a separate partition for data formatted with fat32 or NTFS. This would prevent FS corruption from buggy drivers, upgrade to ext4 without compatibility problem and avoid messing up OS related files from another (the general priciple is: if they can't see each other they can't harm each other). The disadvantage is you have to decide about how much space give for data and for apps in both system. It depends on the need and on the taste, I'm not suggesting to do so, just consider.
That's the system I have set up - I did that years ago when I started with red hat.

I made a few partitians on my laptop HD just for data and both my linux and windows access those. now that I have Ubuntu it works just as well.

frankly, I wouldn't want my windows to see linux. I don't trust it  :)

---

