---
title: "NTLDR is missing...."
date: 2009-05-09
forum: General Help
---

### Post by FinAkechi on 2009-05-09
Ok so here is where I am at.

320GB SATA & 250 GB SATA

Both of the HDD's give me this error. I have tried formatting them and Zero'ing them out.
I can't install Windows to either one and although Ubuntu goes through the instalation process fine it wont actually boot the OS.
To top it all off if I want to boot to a CD i have to manually hit the F10 key and select the CD drive even though it is selected as first priority in the boot order.

What I would like to to is Dual boot Ubuntu and the Windows 7 RC.

Any and all help is greatly appreciated.

---

### Post by paradigm2 on 2009-05-09
Hmm.  Is there some sort of esoteric mbr/boot sector protection on in the BIOS (usually accessed by a certain key or conmbination at startup) ?

If after installing Ubuntu and rebooting using the CD, will it let you boot using the boot from the first hard disk (or whatever the exact wording) option?

---

### Post by exutable on 2009-05-09
First of all what I would do is unplug one of the drives and narrow it down to just one at first, so that you don't have MBRs overlapping and battling each other.  After that I would definitely take a look at my bios settings and then what did you use to zero it out?

Exutable

---

### Post by FinAkechi on 2009-05-09
BOTH the HDD's have the same problem. I Zero'd both of them out. I have nothing on the HDD's I need to save

oh and No it won't let me manually boot from the one with Ubuntu installed on.  My guess is the  the MBR is seriously messed up on both of them. Which by the way. when I do get this fixed. It's going to be easier to install Windows first then Ubuntu correct?

---

### Post by FinAkechi on 2009-05-09
I used ***dd if=/dev/zero of-/dev/sda bs=10MB count=1*** in a terminal off a Ubuntu Live cd

---

### Post by FinAkechi on 2009-05-09
wewt fixed it! good old Windows Recovery console. thank you for the help though guys.

---

### Post by paradigm2 on 2009-05-09
> **FinAkechi said:**
> wewt fixed it! good old Windows Recovery console. thank you for the help though guys.

Glad you fixed it. :) For anyone else who might be searching for this solution in the future, what exactly did you do in the Windows recovery console?  Something like 'fdisk /mbr' ?

---

### Post by FinAkechi on 2009-05-09
> **paradigm2 said:**
> Glad you fixed it. :) For anyone else who might be searching for this solution in the future, what exactly did you do in the Windows recovery console?  Something like 'fdisk /mbr' ?

Lol well I THOUGHT i had fixed it but....

What I had done was a couple of things in the RC

Fixboot C: (or whatever your drive name was)

FixMBR

COPY D:\I386\NTLDR C:\

COPY D:\I386\NTDetect.com C:\

Which had allowed me to install The Windows 7 Ultimate Release Candidate to the 250gb SATA and Ubuntu 9.0.4 to the 320gb SATA. But  heres is where I run into a minor inconvience.

I am still getting "NTLDR is missing Press CTRL+ALT+DELETE to reboot" error. if I manually boot from either the 320 or 250 it will bring me to grub and i can load up either OS no problem, so it's not exactly stopping me from using the PC. But at this point I am not sure what else to do : /.

---

### Post by FinAkechi on 2009-05-09
bump

---

### Post by joereith on 2009-05-09
there is a little iso file that you can burn and then run it is call ntldr fix. Download it frm here and read the documents on how to use it. It is an iso so burn and boot and try it. It worked wonders for me and never had the problem again. [http://tinyempire.com/notes/files/fixntldriso.zip](http://tinyempire.com/notes/files/fixntldriso.zip)

---

### Post by FinAkechi on 2009-05-09
Gah! gunna pull out my hair with this one, still wondering why it wont boot from the CD/DVD drive first.

I am wondering if i, going to have issues with th NTLDR fix disk being that i am using Windows 7

---

### Post by HavocXphere on 2009-05-09
Check the RAM...I've seen the same message on PCs with bad RAM. Why bad RAM would cause *that* error is still a mystery to me but I'd def check it with memtest.

---

### Post by FinAkechi on 2009-05-09
Well My RAM is relatively new so man I hope its not that :(. 

I would upgrade my Comp altogether if i could in all honesty

---

### Post by FinAkechi on 2009-05-09
Ok, SO I think I am completely done with Windows at this point. All I want to do now is Boot up Ubuntu and I'll use the other HDD as extra space. Aside from Completely zeroing out the HDD and is there anythign else i should attempt to get these HDDs back into a pristine state?

---

### Post by FinAkechi on 2009-05-09
Yeah, I really feel lost at this point.
I have tried every little thing I know. Nothing seems too work.

I cannot get past this. Does NTLDR have anything to do wtih Linux? Or is it somethign leftover from Windows? If so why does my comp seems so attached to it.

---

### Post by zeper2012 on 2009-05-09
I had this error once trying to re-install Windows XP. I had formatted the HD as NTFS and kept getting this error. I formatted the drive as FAT32 and it installed without an issue. NTLDR is actually the NT Loader for Windows. I don't know about the newer Windows install disks but the older ones expected to see the NTLDR file if the disk was formatted with NTFS.
Give it a try and let us know.

---

