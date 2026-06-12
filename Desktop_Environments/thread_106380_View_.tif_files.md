---
title: "View .tif files"
date: 2005-12-20
forum: Desktop Environments
---

### Post by sarah_b on 2005-12-20
I need a .tif viewer program that can view multiple pages in one tif file. I am currently using WinXP "Windows Picture and Fax Viewer". I would use Gimv in Linux but it does not see multiple pages, in fact I do not want to use MS at all and only this prevents me from being 100% Linux on my work computer.

Does anyone know of a Linux program that would be comparable to the MS "Windows Picture and Fax Viewer" ? Something I could install with either apt-get or Synaptic.

---

### Post by rhinomite on 2006-03-03
evince will display multi-paged tif files.

---

### Post by Virtual DarKness on 2008-04-03
> **rhinomite said:**
> evince will display multi-paged tif files.

This doesn't seems to work anymore with version 2.22.0 of evince in Kubuntu 8.04 beta..
any advice? is there any other software that can be used for this? (also other than gimp that on my pc takes lot to load due to extra brushes I've added)

thanks.

Giovanni.

---

### Post by Virtual DarKness on 2008-04-09
seems that this problem is still there also with gnome 2.22.1 .. any advice? :confused:

thanks.

---

### Post by Virtual DarKness on 2008-04-29
Waiting for a fix I'm using gimp to open multi-page tif files.. I've made a simple sh script for opening files from thunderbird that loads gimp in a new instance without loading brushes and other stuff (so it loads faster):

> #!/bin/sh
/usr/bin/gimp -n -d $1

ciao

---

### Post by dcroal on 2008-05-07
See Ubuntu bug 201345 for a description (and a fix) of the Evince problem with multi page tiff files.
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/201345](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/201345)
I can email you an updated evince package if you want.

---

### Post by Virtual DarKness on 2008-05-23
> **dcroal said:**
> See Ubuntu bug 201345 for a description (and a fix) of the Evince problem with multi page tiff files.
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/201345](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/201345)
I can email you an updated evince package if you want.

Thanks for the info; I had forgot to check the bugtracker :P
for now I'm ok using the gimp; good to know that a fix will be released in the next version :)

bye,
Giovanni.

---

### Post by Scunizi on 2008-05-23
But can you print if needed from Gimp?  That is after opening a tiff in Gimp each page is typically in one layer.. How do you print individual layers?

My solution was to install Imagemagick and use convert -monochrome <input_file.tif> <output_file.pdf> .. Evince will open multipage pdf and print them if needed.

---

### Post by hanzj on 2008-05-29
Direct Link is: [http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.22.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.22.2-0ubuntu1_i386.deb)

(Please Click the Thank Me button for this post, if you found it helpful)

---

