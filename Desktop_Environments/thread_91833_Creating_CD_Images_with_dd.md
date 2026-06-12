---
title: "Creating CD Images with dd"
date: 2005-11-18
forum: Desktop Environments
---

### Post by simonjbale on 2005-11-18
Hi, 

 I'm trying to create an iso image from a data CD. I've been using the 
 following command: 


 
dd if=/dev/cdrom of=/tmp/image.iso bs=2048 


 
The file produced is always smaller than the original image which was 
 used to burn the CD. Can anyone explain why? I've tried various 
 solutions such as changing the block size to 4096 bytes. A directory 
 listing is shown below, k3b_0.iso is the original image and image.iso 
 is the output from the dd command. 


-rw-r--r--   1 sjbale sjbale 647102464 2005-11-16 22:13 image.iso 
 -rw-r--r--   1 sjbale sjbale 647129088 2005-11-16 22:27 k3b_0.iso 


Cheers, Simon Bale.

---

### Post by nagilum on 2005-11-18
I don't know why it's smaller but the blocksize does not matter in this respect. It only tells 'dd' how many bytes to read at once, nothing more. 'dd' will read the same amount of data no matter what blocksize is set to.

---

