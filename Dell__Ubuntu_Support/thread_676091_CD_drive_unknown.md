---
title: "CD drive unknown"
date: 2008-01-23
forum: Dell  Ubuntu Support
---

### Post by Go0s3 on 2008-01-23
When attempting to install Ubuntu on my Dell Dimension 8200, I received an error finding the CD drive. I know the drive works, but Ubuntu will not recognize it. Where do I find drivers for this older dell machine. Does Dell make them or is there a good community site where I can find them. 
Alternately I have looked through the /dev folder for something I can point the OS to that will allow use for install and of course there is no /dev/CDROM nor is there a /dev/MCDX.
Any suggestions?

---

### Post by kuja on 2008-01-24
Well, I doubt it will help any, really I do, but for my laptop it is /dev/scd0 is the device.
In all cases /dev/cdrom[1] and /dev/dvd[1] are just symlinks to the real devices....

---

### Post by wobbiebobbie on 2008-01-29
hello I just put ubuntu on my dell dimension 8200, it was easy , hit me up and maybe I can help you

---

### Post by Go0s3 on 2008-02-04
What Cd/DVD rom configuration do you have in your Dell? I have windows running for now and can see that the main CD drive that boots the install disc is a nec nr 7900a. However, when the install begins Linux does not see the either of the 2 drives in there.
 What are your Dells full specs? Does it have RDRAM? A P4? Video card (does it run the advanced graphics portion of Ubuntu)? Just out of curiosity.

---

