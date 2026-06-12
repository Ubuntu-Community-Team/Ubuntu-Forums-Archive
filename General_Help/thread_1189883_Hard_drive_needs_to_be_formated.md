---
title: "Hard drive needs to be formated??"
date: 2009-06-17
forum: General Help
---

### Post by s4stevo on 2009-06-17
I go back and fourth between windows and ubuntu. I have used my external hard drive in a while but i needed it yesterday and it worked fine. I downloaded some movies onto it over night. I didn't really check it before I shut it off. When I went to use it in the afternoon I went to click on it and it said "You need to format the disk in drive J:/" or something close to that. That was in windows. I don't know what the response in ubuntu is. I don't know what to do because I have almost 3 gb of stuff on that hard drive. It contains everything from old family pics to songs of AC/DC including about twenty backed  of movies. What can I do about this?? I can not replace a good twenty percent of the stuff on that hard drive.

---

### Post by s4stevo on 2009-06-17
I meant to say "I have not used my hard drive in a while"

---

### Post by Celauran on 2009-06-17
The first step, I'd think, would be to boot into Ubuntu and see if it recognizes the drive. If it does, you can just copy everything from the external drive to your internal hard drive and formatting is no longer a problem.

---

### Post by s4stevo on 2009-06-17
I will try that but is there another solution?

---

### Post by egalvan on 2009-06-18
How is the drive formatted?

Is it Linux or MS format?

---

### Post by bodhi.zazen on 2009-06-18
First step is to stop using the drive and if possible make an image of the contents.

This is a Linux forums, if you wish to use windows and windows tools you may have better luck as I am not familiar with windows applications.

I can, however, advise several linux techniques when you are ready to try them.

---

### Post by s4stevo on 2009-06-18
I'd really like some help because it does not even show up on ubuntu. I don't know whats wrong. Will I have to format it?

---

### Post by Amilo1718 on 2009-06-18
how's it connected?
network or usb?

---

### Post by bodhi.zazen on 2009-06-18
OK, lets take a deep breath :)

Not showing up does not mean much. 

I will caution you, if you are not familiar with partitioning and mounting it will require some reading.

Basically try to mount it manually and see what if any error messages you get.

I also advise you look at testdisk and photorec.

To list your partitions :

```
sudo fdisk -l
```

My guess is  the device is /dev/sdb1

so try to mount it :

```
sudo mkdir /media/restore
sudo mount /dev/sdb1 /meida/store
```

It will either mount or more likely return an error message.

```
dmesg | tail
```

If the device will not mount, best make a back up image, with dd This back image will be as large as the external hd, so you need space on your HD to store it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

If yo format the disk you will loose all your data =)

---

### Post by s4stevo on 2009-06-18
Its connected by USB. Bodhi.zazen, I will try that right after I finish with something else. I did some searching when I thought of treating my external hard drive as if the files were currupt or deleted so I look for some data recovery program. I don't know if you have heard of it, its called R-Studio network edition? I'm reading about it now and I think it may be able to help me.

---

### Post by s4stevo on 2009-06-18
How do I go about creating a partition in the hard drive?

---

### Post by bodhi.zazen on 2009-06-18
Assuming you have free space, I use gparted.

It is on the live CD. boot the ubuntu CD, make your windows partition smaller, and in a second step make a new partition in the resulting free space.

You will then need to mount the partition. This may or may not be automatic in Windows, in Ubuntu you will need to make a directory and mount it.

```
sudo mkdir /media/recovery
sudo mount /dev/sda2 /media/recovery
```

---

### Post by s4stevo on 2009-06-20
I plug this hard drive into ubuntu and it doesn't even appear, whats with that?

---

### Post by camper365 on 2009-06-20
When you say it doesn't appear, does that mean that it doesn't appear in the Places menu or the /dev folder. Post the output of ```
sudo fdisk -l
```

---

