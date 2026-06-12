---
title: "Urgent partitioning help needed"
date: 2009-03-23
forum: General Help
---

### Post by thomasboleyn on 2009-03-23
Hi there, a couple of days ago I bought this laptop [http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1803274037.1237835610@@@@&BV_EngineID=ccdiadegkghifdjcflgceggdhhmdgml.0&page=Product&fm=null&sm=null&tm=null&sku=854274&category_oid=-35054](http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1803274037.1237835610@@@@&BV_EngineID=ccdiadegkghifdjcflgceggdhhmdgml.0&page=Product&fm=null&sm=null&tm=null&sku=854274&category_oid=-35054) (in silver not pink!) and promptly installed Xubuntu on it, which works absolutely flawlessly, even the webcam. Using the live cd I gave the majority of the 300 gig hard drive to Xubuntu. I've now (already) got the stage in windows where I have run out of hard drive space, and urgently need to know how to shrink the Xubuntu partition and give some back to Vista. Neither the partion tool in Vista, or Gparted seem to allow me to do this, and I am now stumped as to what to do. I'm really not experienced with stuff like this, and I imagine it's probably quite simple to do. Any help would be greatly appreciated. 

Here is a screenshot of Gparted to help: [http://i41.tinypic.com/3127mmd.png](http://i41.tinypic.com/3127mmd.png)

---

### Post by Wicca on 2009-03-23
Hi,

You cannot resize partitions when they are mounted. Boot from a liveCD and try to resize from there.
You may need to install gparted first.

Good luck.

---

### Post by Therion on 2009-03-23
Download, and burn to a bootable CD, Parted Magic (the new name for gPartEd):

[http://download.cnet.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html](http://download.cnet.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html)

Boot to same, adjust partitions as desired, get on with Life...


Joy!

---

### Post by lindsay7 on 2009-03-23
I am having the same problem and have an open post hoping to find a solution. From the little that I have found, it seems to be a problem with the partition you and I are trying to shrink being ext3. If I get some info that would help, I will post a ink for you here. I will follow your post and hope you get help.

---

### Post by Therion on 2009-03-23
As has been pointed out already you can't adjust partitions on the hard drive you've booted from because you can't adjust (e.g. resize, move, etc.) a partition while it's mounted.

*vis-a-vis*... Booting mounts partitions.

Hence, you boot to a LiveCD (partitions stay UNmounted) and you can move, resize, etc. to your heart's content.

---

### Post by lindsay7 on 2009-03-23
I have been trying to do the repartitioning with the Ubuntu live cd. Did I do something wrong or is there another step to take.

Thanks for the help.

---

### Post by Al Fischer on 2009-03-23
So do what you were told. Download the GPARTED live CD, burn it to a CD and boot from it. NOT from Ubunt or Windows. It works.

---

### Post by Therion on 2009-03-23
> **Al Fischer said:**
> So do what you were told. Download the GPARTED live CD, burn it to a CD and boot from it. NOT from Ubunt or Windows. It works.
Thank you.

---

### Post by boof1988 on 2009-03-23
> **lindsay7 said:**
> I have been trying to do the repartitioning with the Ubuntu live cd. Did I do something wrong or is there another step to take.

Thanks for the help.

One thing you might (will?) need to do, if you are using the Ubuntu LiveCD, is to turn the swap partition off (in gparted).  This can be done by choosing the parting and either right-clicking or the menu and choose swap-off (or similar).

This may not be what is causing your problems, but this info may help you or someone else.

---

### Post by lindsay7 on 2009-03-23
Ok, thanks to all for clearing this up for me. From other threads that I have been reading, I lead myself to belive that you could do this from the Ubuntu Live cd. It is clear now that one should run Gparted or Partition Magic from its own cd or do as you said and turn off the swap partition.

It is like I tell my son, once you know the answer, the question is easy!

Thanks again.

---

### Post by Al Fischer on 2009-03-23
CAUTION  DO NOT CONFUSE [COLOR="Red"]PARTITION MAGIC [/COLOR]WITH GPARTED.  

Partition Magic is a 'pay for product' and GPARTED is FREE for the time to download and the cost of a CD to burn. It is only the BEST partitioning tool I have seen in YEARS!! IT WORKS!! (or rocks if you prefer)

---

### Post by lindsay7 on 2009-03-23
Thanks agin for the good advice.

---

### Post by Al Fischer on 2009-03-23
One more thing. If you are not knowledgeable of partitioning there is a lot of info on the net. Google for it, read it, you will benefit greatly. Not really difficult. Don't hesitate to ask questions, there is much to be learned here.

---

### Post by thomasboleyn on 2009-03-24
So Gparted is officially, **really slow**. To shrink my main partition by roughly 80gb it has taken over 3 hours already, and it is apparently going to take another 5 and a half. Joy.

---

### Post by thomasboleyn on 2009-03-25
Ok, I'm stuck again now. I need to combine the newly created 77.60gb partition with the 54.09gb partition with Vista on. Using the Gparted live cd I don't seem to be able to do this. All options seem to be greyed out. Below is a screenshot of gparted running inside Ubuntu (I am aware that to do anything I need to use the live cd, I'm just using these screenshots for convenience). Any help would be greatly appreciated!

[http://i43.tinypic.com/jpeqmw.jpg](http://i43.tinypic.com/jpeqmw.jpg)

---

### Post by lindsay7 on 2009-03-26
If I understand this correctly, it looks like you need to unallocate sda6 and then grow or increase sda2 to fill the space.  Here is some info that my clear this up for you, it is at the very end of the article.  Hope it helps.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Slim Odds on 2009-03-26
> **thomasboleyn said:**
> So Gparted is officially, **really slow**. To shrink my main partition by roughly 80gb it has taken over 3 hours already, and it is apparently going to take another 5 and a half. Joy.

**Any** partitioning software that needs to move that much data and rearrange the file system will be slow.

---

