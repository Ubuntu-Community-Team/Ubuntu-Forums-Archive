---
title: "Can't Ubuntu copy audio CDs?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Zunino on 2006-09-15
Hello.

From some googling I learned that one may quickly copy a CD to an image file by right-clicking the CD icon and choosing "Copy Disc...". The same resources mentioned that burning the extracted images later on was just a matter of right-clicking them and choosing "Write to Disk...".

"That couldn't be easier!", I thought. However, as nice as it might seem, my very first CD copying attempt failed. I inserted the original CD (an unprottected audio disc) and proceeded as described above to generate a file image. I named the image Test.iso and chose the Desktop as the target directory. The copying process ended and I noticed an auxiliary file had also been created, namely Test.iso.toc.

Next, I inserted a blank CD, right-clicked on the Test.iso file and chose "Write to Disk...", only to get an error dialog box telling me the file contained an invalid image. I tried repeating the process with other audio CDs, but got the same results. Then I decided to try it with a data CD; this time it worked, to my surprise.

Some preliminary searches on the problem suggested that generating images from audio CDs was somehow different from doing the same thing with data CDs. One or two posts mentioned the need for special tools, such as cdrdao, when dealing with audio CDs. Pardon my ignorance, but does it really make sense? Aren't CD images independent of the nature of the data? I thought an ISO CD image was simply that: an image of a CD, be it a data one or an audio one.

Could anybody shed some light on this issue? I would really like to understand what's going on here. If audio CDs actually require a special method for extracting their image, then I think Nautilus should make that need explicit somehow. But, again, I don't believe that's the case.

Thank you very much,

-- 
Ney André de Mello Zunino

---

### Post by canadianwriterman on 2006-09-15
Have you tried Gnomebaker? It's in the repositories and works well for me.

---

### Post by Zunino on 2006-09-15
> **canadianwriterman said:**
> Have you tried Gnomebaker? It's in the repositories and works well for me.
Thanks for the suggestion. I am aware of such tool and will probably end up using it, if the "built-in" solution does not work. Nevertheless, I would still like to understand what's going on and to learn more about the differences (if any) between copying audio and data CDs. I see Gnome/Nautilus' solution of providing "Copy Disc..." and "Write to Disk..." commands as quite simple and elegant and that's why I would rather use it as opposed to relying on external tools. Of course, it should ideally work out-of-the-box, without any need for tweaking.

Regards,

-- 
Ney André de Mello Zunino

---

### Post by canadianwriterman on 2006-09-15
I'm in the process of trying it the way you did. The first thing I noticed is that it gives me the option of burning a CD directly, rather than creating an image first. Is there a reason that you wanted an image first?

---

### Post by Zunino on 2006-09-15
> **canadianwriterman said:**
> Is there a reason that you wanted an image first?
Yes. I am supposed to make many copies of the disc. It seemed to me the most effective way to go would be to extract its image first and then burn it to the target CDs.

I am looking forward to hearing about your findings.

Regards,

-- 
Ney André de Mello Zunino

---

### Post by canadianwriterman on 2006-09-15
Okay, this copying is taking forever. I did check out the cdrao reference you mentioned and found this. It might be the problem:
[URL="http://cdrdao.sourceforge.net/"]
http://cdrdao.sourceforge.net/
[/URL]

---

### Post by peabody on 2006-09-15
> **Zunino said:**
> Pardon my ignorance, but does it really make sense? Aren't CD images independent of the nature of the data? I thought and ISO CD image was simply that: an image of a CD, be it a data one or an audio one.


Unfortunately I believe it does.  Someone was trying to create an image file of a playstation game rom and couldn't get it to work with standard tools.  Something about Playstation rom discs being multitrack or some such.  I believe ISO is just one of many different filesystems that can be put on a CD.  ISO is the most widely available common denominator so its ubiquitous for things like Linux ISO's and stuff, but there are other types of images.  Others include Microsoft Joilet, ufs or udf (can't remember which), and other types.  I think that's the big deal with .bin files.  They're a format for a completely raw image of what's on a disc, independant of the filesystems.

---

### Post by canadianwriterman on 2006-09-15
Copying the disk image is stalled at about 25 minutes. It doesn't seem to be doing anything more. But, I'll leave it and see what happens.

---

### Post by Zunino on 2006-09-15
> **canadianwriterman said:**
> Copying the disk image is stalled at about 25 minutes. It doesn't seem to be doing anything more. But, I'll leave it and see what happens.
I am calling it a day, but I will surely check back here tomorrow. Thank you (and peabody) very much for your kind assistance.

Regards,

-- 
Ney André de Mello Zunino

---

### Post by canadianwriterman on 2006-09-15
No love. Image burning sticks part way through and will not continue. In that sense, you had better luck than I did. I tried some other methods for quickly ripping the tracks and burning CDs (such as using the default Soundjuicer to rip the tracks, then Serpentine to burn CDs, but the tracks are converted to ogg format, not the original format on the CD. Sorry.

---

### Post by Zunino on 2006-09-16
Thanks again, canadianwriterman. Some more research showed me that there's more to CD images than I initially believed. In short, the ISO format is not suitable for multi-track image formats, such as CDDA [1]. That would explain why the "Write to Disk..." function fails.

It seems the way to go is to use the .BIN/.CUE pair, which deals with RAW CD data and, as far as I have understood, should work with any kind of CD.

Nevertheless, I still think the Ubuntu desktop should warn the user about the impossibility of making an ISO image out of an audio CD or, ideally, know how to handle that case as well.

[1] [http://en.wikipedia.org/wiki/Disk_image#Formats](http://en.wikipedia.org/wiki/Disk_image#Formats)

Best regards,

-- 
Ney André de Mello Zunino

---

### Post by Zunino on 2006-09-16
Just to make sure other people reading this thread in the future will find something to help them, here's what I ended up doing to make raw copies of the original audio CD.
```
cdrdao read-cd --read-raw --datafile /tmp/MyCD.bin --device ATAPI:0,0,0 --driver generic-mmc-raw /tmp/MyCD.toc
```
The above command will create a raw image of the audio CD, saving it in the /tmp/MyCD.bin file. An auxiliary file, /tmp/MyCD.toc will also be created.

Having done that, the generated pair bin/toc can be used to burn exact copies of the original CD, with the following command:
```
cdrdao write --device ATAPI:0,0,0 /tmp/MyCD.toc
```
I hope that helps,

-- 
Ney André de Mello Zunino

---

### Post by egd on 2007-06-13
> **Zunino said:**
> ...here's what I ended up doing to make raw copies of the original audio CD.
```
cdrdao read-cd --read-raw --datafile /tmp/MyCD.bin --device ATAPI:0,0,0 --driver generic-mmc-raw /tmp/MyCD.toc[/code

For ease of use, inserting an audio CD then right-clicking on the CD icon on the Desktop and selecting copy CD does the same.

> **Zunino said:**
>  Having done that, the generated pair bin/toc can be used to burn exact copies of the original CD, with the following command:
[code]cdrdao write --device ATAPI:0,0,0 /tmp/MyCD.toc
```

Thanks, that helped me.  Anyone running a recent version of Ubuntu can reference the CD Burner directly as follows:  ```
**cdrdao write --device /dev/scd0 filename.toc** 
``` - where **/dev/scd0** happens to be my burner.

---

