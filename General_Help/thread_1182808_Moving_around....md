---
title: "Moving around..."
date: 2009-06-09
forum: General Help
---

### Post by null.byte on 2009-06-09
Okay, here's the deal: I have a computer running Windows XP. It's HDD has 80GB, and it is partitioned like this:
- C: - 20gb
- D: - 60gb
On D: I have 12.3GB filled with music. I want to install Linux on that computer, and to completely erase Windows... but how can I keep the files? I do not have DVDs, external HDDs, nor I want to buy.

Thanks in advance.

---

### Post by buchan on 2009-06-09
If I'm reading this right you have a 20 Gb partition that has windows (c:\) and a 60 GB partition with your music (d:\)

The C:\ partition can be formatted and used however you want

The D:\ partition is formatted with NTFS with 12.3GB of music.
 

Its a bit of a run around but here's how I would do it:
Install Ubuntu on the 20GB partition and do not touch the 60GB partition at all, You could set it up as a mount point like /music during the setup.  As its NTFS (please feel free to correct me here its been a while) you will only be able to read from this disk.  

Once the system is up and running you should have enough room to copy the Music disk to somewhere on your 20GB as Ubuntu should leave enough space.  
```
rsync -av /ORIGINAL-LOCATION /TEMP-LOCATION
```

Then format the 60GB with EXT3-4 (your choice) and copy your music back to the 60 GB disk.  
```
mkfs.ext3 /dev/DDRIVE
mount -t /dev/DDRIVE /Music
(you'll also want to modify your /etc/fstab file accordingly here)
rsync -av /TEMP-LOCATION /ORIGINAL-LOCATION 

```


This way you can add music to your collection as well as keeping the existing stuff too.  Hope this makes sense, post back if you have any questions.

---

### Post by Tipped OuT on 2009-06-09
Just move your files to the 20 GB partition, then move them back after you install Ubuntu on the 60 GB 
partition. I suggest compressing them into a RAR file.

---

