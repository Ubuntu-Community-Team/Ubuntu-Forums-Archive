---
title: "Data Recovery Software (Cannot mount home)"
date: 2009-01-31
forum: General Help
---

### Post by davidbilla on 2009-01-31
Hi,

The superblocks in my /home partition have gone bad. I'm using the OS(Ubuntu, of course!) in my external HD now to boot. I want to recover only certain folders from my corrupted /home partition in my internal HD. I don't want to backup the entire partition using dd or ddrescue. Using 'testdisk', I can view my files in that partition. Now, from what I gather, there are s/w to image your entire partition or software which recover deleted files. But, what I want to do is a data recovery s/w which can recover the UNDELETED EXISTING folders inside a corrupted partition. I don't care about other folders and I don't want to make an image of the entire 30 GB partition. Is there a way to do this? If there is, can someone explain it in a little bit of detail?

Thanks.

---

### Post by davidbilla on 2009-01-31
OK. Can anyone give me an example as to how to use GNUddrescue-'ddrescue'?

Can I give the output file option as a directory? Or can I create an iso image? Or do I have to create an '.img' file? Examples...

Thanks.

---

### Post by albinootje on 2009-01-31
With CloneZilla you can use compression for the resulting clone image.
Try it : [http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Bigneil on 2009-01-31
what about Photorec, would that pull out your files and copy them to you external drive.?

---

### Post by davidbilla on 2009-01-31
> what about Photorec, would that pull out your files and copy them to you external drive.? 

Hi, thanks for replying.

Will photorec recover all files of a given type (say, I choose to recover mpg's or jpg's)that currently exist in the corrupted HD or will it only recover 'deleted' files in that HD?

---

### Post by bumanie on 2009-01-31
Photorec gives one the choice of which file types to look for. It is filesystem independant as it looks at the raw disk, not the filesystem. Go to the testdisk site and on the upper left there will be a link to photorec. You can then find a step-by-step towards the bottom of the page. Read the tutorial to know how to choose which file types to look for.

---

