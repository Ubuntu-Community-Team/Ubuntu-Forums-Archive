---
title: "Help! read only external hd"
date: 2006-07-29
forum: Desktop Environments
---

### Post by glaucon on 2006-07-29
ok so I had windows running on my desktop but I have recently switched to ubuntu for the thrid time and have finnaly got enough functionality to stick with it. however, there is a problem. my desktop is going into storage for a while and I need all of my data. I have a 200g external hd that I keep all my files on and its about 1/2 full. my laptop dosn't have room for all the files so I need to be able to access and change them directly on the external.

but my problem is that ubuntu thinks MY EXTERNAL IS READ ONLY! and it wont let me change the permissions for it! it works on windows just fine and is not read only. please say there is an easy way to fix this! I am far from an expert and have done little in terminal that wasn't cut and paste.

I reallly dont want to go back to windows please help!

thanks in advance - nick

---

### Post by Jagot on 2006-07-29
What file system does the hard disk use?  If it is NTFS then there is no safe way to write to it as Linux does not support it.  There are a few experimental methods around you could search for.  If this is the case, you may want to put the files back on your desktop before it goes into storage and format the disk to FAT32 from Ubuntu, then put the files back on.

---

### Post by glaucon on 2006-07-29
oh no! thats exactly what I was afraid of. I formatted the hd with windows so it probably is. :( if i format it with ubuntu will i be abel to get my files back off my desktop and onto the hd?

---

### Post by Jagot on 2006-07-29
Yep - if you make sure all the files are copied to the desktop first, the format the disk with GParted in Ubuntu to FAT32 (it might be called vFAT - can't remember), then you'll just be able to put your files straight back on.

---

### Post by glaucon on 2006-07-29
thanks a ton im transferring files as we speak! huzzah! that leaves like 2 inperfections left in ubuntu. its so near perfect!

---

