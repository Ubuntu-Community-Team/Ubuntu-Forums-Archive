---
title: "Remastersys don't work!"
date: 2009-05-28
forum: General Help
---

### Post by gcclt on 2009-05-28
I generate Ubuntu 9.04 iso image with **Remastersys**. After this I booted image with VirtualBox, but e get this error in text mode:

"SQUASHFS error: Major/Minor mismatch, older Squashfs 3.1 file systems are unsupported"

PrintScreen of VirtualBox:
**[http://img22.imageshack.us/my.php?image=remastersys.png](http://img22.imageshack.us/my.php?image=remastersys.png)**

---

### Post by bryanl on 2009-05-29
Did you install the latest version from [Remastersys for Ubuntu Information](http://www.geekconnection.org/remastersys/ubuntu.html)? check also the [Remastersys Forum](http://geekconnection.org/remastersys/forums/index.php)

The only problem I had was that an old bug with the system printer configuration showed up after I installed a 9.04 customized and remastered. I haven't checked but that may have been fixed by now. I used the new USB boot disk utility to make a bootable Remastersys stick.

It is intriguing (to me, anyway) to see what has to be fixed in remastersys with each new Ubuntu release. It highlights some of the low level changes.

I see they now have a GRUB restore, too.

---

### Post by gcclt on 2009-05-29
> **bryanl said:**
> Did you install the latest version from [Remastersys for Ubuntu Information]("http://www.geekconnection.org/remastersys/ubuntu.html")? check also the [Remastersys Forum]("http://geekconnection.org/remastersys/forums/index.php")

The only problem I had was that an old bug with the system printer configuration showed up after I installed a 9.04 customized and remastered. I haven't checked but that may have been fixed by now. I used the new USB boot disk utility to make a bootable Remastersys stick.

It is intriguing (to me, anyway) to see what has to be fixed in remastersys with each new Ubuntu release. It highlights some of the low level changes.

I see they now have a GRUB restore, too.

Yes, I do....

I **try** with my other kernel (older version).

Tank's.

---

### Post by gcclt on 2009-05-30
> **gcclt said:**
> Yes, I do....

I **try** with my other kernel (older version).

Tank's.

I tried **again** with the **default** kernel of ubuntu 9.04 but not succeeded. [B]Got the same error.
[/B]

---

### Post by gcclt on 2009-05-31
I had to do liveDVD using the tutorial.  

 [http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html)  

 **Note: No place in the squash used ext2 and worked!!**:D

---

