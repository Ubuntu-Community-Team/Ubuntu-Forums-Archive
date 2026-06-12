---
title: "OS fron CD"
date: 2010-06-18
forum: Desktop Environments
---

### Post by bseidel52 on 2010-06-18
We are trying to create customized Ubuntu systems (with programs and settings preset) to run on systems without a hard drive. we are running Ubuntu 10.04 using Pixi boot and need to have a backup in case our provisioning server  (part of our SLAs)
I know Ubuntu can be run from the install disk but that is not modified and won't suffice for our needs. any suggestions
I have created other bootable OS's but, I am fairly new to Ubuntu

---

### Post by oldfred on 2010-06-18
If you can boot from USB flash drives that would be the easiest way. You can do a full install to the flash drive.

If you have to have CD, I have seen recommendations for remastersys, but never used it.

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by C.S.Cameron on 2010-06-18
Once you have the flash drive how you want it, it can be cloned using dd.
Or you can use usb-creator to install a remastered iso to flash drive.

---

### Post by bseidel52 on 2010-06-18
I tried this but, it acts just like the install cd and also i need this to be on a cd not a flash drive

---

### Post by Silviner on 2010-06-18
Hi, Im not sure if this what youre looking for,but it might help.
I have seen an example of this on the following link:

[http://www.freshtings.com/bootsector.html](http://www.freshtings.com/bootsector.html)

but as previous poster said the dd command I have seen work as well. 

I think, but am  not sure(i.e. you will have to investigate) it goes something like:

dd if=/dev/cdrom of=/tmp/mycdimage.iso

disclaimer: this is only a recommendation of a novice!

I am doing something similarto yourself  but I'm using a hex editor called 010 Editor to copy ASM code to CD. 

best of lluck with it tho!.

---

### Post by Shazzam6999 on 2010-06-18
This kind of already exists in Remastersys, although I don't have a lot of knowledge about it.

"Remastersys is a free and open source script for Debian, Ubuntu-based, or derivative software systems that can:
Create a customized Live CD/DVD (a remaster) of Debian and its derivatives.

Back up an entire system, including user data, to an installable Live CD/DVD."

Quoted from Wikipidia so you know it's reliable.
[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by bseidel52 on 2010-07-02
I appreciate everyones input but, all of the above boot to a CD with a trial OS or asks to install Ubuntu. this is not what I want to do. when the terminal boots it either goes to a Pixie boot or to the CD drive (NOT DVD), there are no other options. I have made many boot - run OS CD for other platforms but this one has me stumped.

---

