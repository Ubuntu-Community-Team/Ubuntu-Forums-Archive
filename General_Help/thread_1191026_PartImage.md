---
title: "PartImage"
date: 2009-06-18
forum: General Help
---

### Post by Geffers on 2009-06-18
Long shot here but hoping someone may be able to assist with use of PartImage. The PartImage forum does not seem too active.

On the second screen under 'Compression Level' Gzip is selected by default, no key or combination of keys I have tried will alter this default value.

Does anyone know how I can select No Compression or Bzip2

Geffers

---

### Post by VMC on 2009-06-18
> **Geffers said:**
> Long shot here but hoping someone may be able to assist with use of PartImage. The PartImage forum does not seem too active.

On the second screen under 'Compression Level' Gzip is selected by default, no key or combination of keys I have tried will alter this default value.

Does anyone know how I can select No Compression or Bzip2

Geffers

./partimage -z1 -o -d save /dev/sdaX /media/SDAsomething/Image.gz

z1: Use the gzip algorithm to compress the image. z0 means no compression and z2 means usage of the bzip2 algorithm, but it’s slower.

Or are you using the TUI version?

---

### Post by Geffers on 2009-06-19
> **VMC said:**
> ./partimage -z1 -o -d save /dev/sdaX /media/SDAsomething/Image.gz

z1: Use the gzip algorithm to compress the image. z0 means no compression and z2 means usage of the bzip2 algorithm, but it’s slower.

Or are you using the TUI version?

Thanks, I'll give that a try.

TUI, is that a typo, did you mean GUI?

If so yes that was what I tried first but the command line looks easy so I will give it a try.

Geffers

---

### Post by Geffers on 2009-06-20
> **Geffers said:**
> Thanks, I'll give that a try.

TUI, is that a typo, did you mean GUI?

If so yes that was what I tried first but the command line looks easy so I will give it a try.

Geffers

Initially looked good, the image saves but doesn't appear to restore properly.

I'm thinking the dd command may be preferable.

Geffers

---

### Post by indytim on 2009-06-20
Use the GUI

```

$sudo partimage

```

See my website under backup strategy for my detailed information on use of Partimage (at the tail end of the paper). 

IndyTim

p.s I use it weekly to back up my active ops etc.

---

### Post by Geffers on 2009-06-21
> **indytim said:**
> Use the GUI

```

$sudo partimage

```

See my website under backup strategy for my detailed information on use of Partimage (at the tail end of the paper). 

IndyTim

p.s I use it weekly to back up my active ops etc.

Will read your guide but re partimage; on the GUI I cannot get any keyboard input for some optional fields such as the following;

```
 Action to be done:                                <Next (F5)>     &#9474; 
     &#9474; (*) Save partition into a new image file                          &#9474; 
     &#9474; ( ) Restore partition from an image file          <About>         &#9474; 
     &#9474; ( ) Restore an MBR from the imagefile     
```

I cannot seem to alter Save Partition to Restore Partition and on the following page there are options to alter the compression, my keyboard doesn't alter those either.

I don't have a keyboard problem though.

Geffers

---

### Post by Geffers on 2009-06-21
> **Geffers said:**
> 

I cannot seem to alter Save Partition to Restore Partition and on the following page there are options to alter the compression, my keyboard doesn't alter those either.

I don't have a keyboard problem though.

Geffers

After reading your web site I found I pressed every key EXCEPT the space key to alter options.

Thanks for pointer and I'll give partimage another go.

Have you any views how reliable it is with NTFS partitions as I wouldn't mind backing up a Vista OS as well as my Linux OSs.

Geffers

---

### Post by indytim on 2009-06-21
I personally have not used it to restore a NTFS partition.  The last time I checked, the developer had flagged it as "experimental".  If you do try it, it would be good to post back your experiences for the benefit of the collective.  As experimental, I would recommend only trying it on a partition that you can afford to loose if it doesn't succeed.

I have used it numerous times to restore ext3's with no problems.  It's been my experience that it takes about 3-5 minutes of run time to restore a ~5G partition.

IndyTim

---

### Post by Geffers on 2009-06-22
> **indytim said:**
> I personally have not used it to restore a NTFS partition.  The last time I checked, the developer had flagged it as "experimental".  If you do try it, it would be good to post back your experiences for the benefit of the collective.  As experimental, I would recommend only trying it on a partition that you can afford to loose if it doesn't succeed.

I have used it numerous times to restore ext3's with no problems.  It's been my experience that it takes about 3-5 minutes of run time to restore a ~5G partition.

IndyTim

Re the suggestion to post my experience on the NTFS backup.

The Vista machine is a new laptop and I'm not sure how I can check if any saved image is successful.

I have saved ext3 from a a working bootable USB key and restored it to an  external USB drive but this drive will not boot. The filesystem appears to be there but even using manual GRUB commands I cannot boot it.

If I set the root directory and then try the GRUB setup (hdn) it says Unable to mount partition.

Geffers

---

### Post by Geffers on 2009-06-29
> **indytim said:**
> If you do try it, it would be good to post back your experiences for the benefit of the collective.  
IndyTim

Well, gave it a try and it states it has successfully saved the image files.

It was a 220GB NTFS drive, Vista properties showed 34GB used though even counting hidden and system files I cannot get anywhere close to 34GB but partimage has saved 80GB.

I don't want to try a restore on a new laptop so I may just restore to a spare HD and see if the filesystem appears intact.

Geffers

---

