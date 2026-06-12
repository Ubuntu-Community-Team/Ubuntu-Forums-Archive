---
title: "How do I restore the original MBR to boot Vista?"
date: 2007-12-22
forum: Dell  Ubuntu Support
---

### Post by JohnnyBoy022 on 2007-12-22
I am about to install Ubuntu to an external hard drive. I am kind of paranoid that I might somehow mess up the MBR on my internal drive, even though I plan to install GRUB on the external's MBR.

If I mess up the MBR on the internal drive, how can I restore it to the original windows MBR? All the answers I have found say to insert the vista disk and there is something on it that will restore it. But I didn't get a Vista disk when I bought my computer from Dell, it was already pre-installed. I can't seem to find any information from the Dell website, so any help would be appreciated. Thanks!

---

### Post by meierfra on 2007-12-22
Click on FixMBR in my signature.

---

### Post by meierfra on 2007-12-22
I recommend to physically remove the internal drive before you install ubuntu.(inparticular if you have a SATA and an IDE drive)

---

### Post by JohnnyBoy022 on 2007-12-23
Thanks for the link. I have a laptop, is there anyway to disconnect the internal drive?

---

### Post by meierfra on 2007-12-23
On my laptop all I have to do is unscrew a couple of screws and then the hard drive slides right out. Do you have a manual for your laptop?  It should tell you how to do it. (If not google might find one for you)

---

### Post by gbrainin on 2007-12-23
> **meierfra said:**
> Do you have a manual for your laptop?  It should tell you how to do it. (If not google might find one for you)

Hardware manuals are available on Dell's support website: [http://support.dell.com/]("http://support.dell.com/")

---

### Post by JohnnyBoy022 on 2007-12-23
> **meierfra said:**
> On my laptop all I have to do is unscrew a couple of screws and then the hard drive slides right out.

It looks like mine is the same as yours, just unscrew two screws and it comes out. If you don't mind, what is the reason for taking the hard drive out? Just so there is no chance for a mistake?
I also looked at that link you posted, and it looks like I would have to make s superGRUB disk because I don't have the vista installation disk. Thanks for the help.

---

### Post by meierfra on 2007-12-23
> also looked at that link you posted, and it looks like I would have to make s superGRUB disk because I don't have the vista installation disk.

Getting SuperGrub is always a good idea. But the third method can be done from either Ubuntu or from the Ubuntu LifeCD and does not require the VistaCD.

---

### Post by logos34 on 2007-12-23
> **meierfra said:**
> Getting SuperGrub is always a good idea. But the third method can be done from either Ubuntu or from the Ubuntu LifeCD and does not require the VistaCD.

SuperGrub can restore the Vista bootloader/mbr?  I didn't know there was a way other than Vista install DVD.

---

### Post by meierfra on 2007-12-23
> SuperGrub can restore the Vista bootloader/mbr? I didn't know there was a way other than Vista install DVD.

As far as I know the Vista MBR is the same  as the  XP MBR. It just chainloads the active partition. Also I have seen people in the  forum  fixing the Vista MBR with Supergrub and also with ms-sys.
(Although the Vista boot sector is different from XP. So fixing the boot sector probably does not work with SuperGub. But since Ubuntu will not touch the boot sector this should  not be an issue)

---

### Post by logos34 on 2007-12-23
Hmm...So the mbr (or to be more precise the IPL) restored by sgd or my-sys will boot vista (i.e. -->boot manager/loader on bootsector of vista partition).  You don't need to do it from the vista install dvd repair environment.  If only I'd kept my downloaded copy of vista RC1 I'd have known this a long time ago...

---

### Post by JohnnyBoy022 on 2007-12-24
Looks like the problem is solved!
[This link]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=28D6863EBF509D7DE040A68F5B286451&doclang=en&cs=") should help out anyone else who is having this problem. Dell has a utility you can download and put on a cd to fix the MBR.

---

### Post by meierfra on 2007-12-25
Sorry, but in my opinion SuperGrub is the better option. It can fix your MBR and can  reinstall Grub as well.

---

