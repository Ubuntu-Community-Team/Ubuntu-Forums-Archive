---
title: "Upgrading to next Version of Kubuntu without Reinstall?"
date: 2005-10-10
forum: Desktop Environments
---

### Post by SadaraX on 2005-10-10
I just downloaded and installed Hoary on my computer yesterday. I want to know how I would upgrade my system to the next version of Kubuntu when it comes out, without having to download the CD iso and install my whole system again.

---

### Post by aysiu on 2005-10-10
It's easy. You ```
sudo kwrite /etc/apt/sources.list
``` Do a find/replace on the word *hoary* for *breezy*, save the file, then type this in the terminal ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Chareos on 2005-10-10
Anyone tried? and... survived ? ^_^
Please post your experiences in upgrading kubuntu from hoary to breezy.

---

### Post by stimpack on 2005-10-10
Tried and fried = once :mad: 
Tried and won = once :)

---

### Post by manubreizh on 2005-10-10
upgrade like this, replacing hoary with breezy ; but i've had some trouble with kde3.5 beta, which was installed ; i just remove all kde3.5 and install kde from breezy repositories, but in command line and with some apt-get knowing (install, remove, names of paquages, vi and so on) ; finally it worked, but i think i'm lucky to know a few line code commands !

---

### Post by B.B on 2005-10-10
Done it on 3 computers (2 of them are laptops) over the last couple of weeks. Still going strong, but then again, im a rookie when it comes to linux, so i proberbly wouldnt know if its not working the way its surposed to do.  ;0)

None the less my experience from the other side (Microsoft land) says: Never never never upgrade an entire OS, reinstall, and thats what ill do when the 5.10 final comes out.

---

### Post by SadaraX on 2005-10-10
I suppose one of the easiest methods to ensure a safe upgrade is save my home directory, then install the next version (breezy) with formating everything. Install all my regular programs and then copy my home folder back over the new version home. 

I kind of wish there was an option for "preserve your home directory" while installing the upgrade for ubuntu/kubuntu.

---

### Post by mpettitt on 2005-10-10
There is a way to preserve home directory when upgrading, but it takes a little forethought. When installing initially, create 2 partitions on your hard drive, one for the / folder, and one for /home. Then, whenever you need/want to reinstall, just tell the installer to not format the /home partition and to mount it as /home.

When you finish the install, your system will be fresh but your data will still be there! Of course, if you have managed to cause some corruption through something in /home (not sure how you would do this, but I suppose it is possible), it will still be there.

---

### Post by Takis on 2005-10-10
[QUOTE=mpettitt]There is a way to preserve home directory when upgrading, but it takes a little forethought. When installing initially, create 2 partitions on your hard drive, one for the / folder, and one for /home. Then, whenever you need/want to reinstall, just tell the installer to not format the /home partition and to mount it as /home.[/QUOTE]
So how would you do this under Windows?

Oh, wait - you *can't*. Ye gods, I love Linux.

---

### Post by ltmon on 2005-10-10
[QUOTE=Takis]So how would you do this under Windows?

Oh, wait - you *can't*. Ye gods, I love Linux.[/QUOTE]

Well... I think you can pretty much do the same thing, at least I've seen an install of Windows XP where the "Documents and Settings" folder was on D: rather than C:

I've got no idea how to manage this myself though, and a five minute Google didn't fix that.

L.

---

### Post by Hobbsee on 2005-10-10
you would have to change where the my docs link was pointing, to the d drive.

To answer the question, one failed, and one that seemed to work fine.  However, i've just clean installed a few days ago for testing a daily cd, and that worked without a problem

---

### Post by Takis on 2005-10-11
[QUOTE=ltmon]Well... I think you can pretty much do the same thing, at least I've seen an install of Windows XP where the "Documents and Settings" folder was on D: rather than C:

I've got no idea how to manage this myself though, and a five minute Google didn't fix that.

L.[/QUOTE]
Yeah but how many programs have 'C:\Documents and Settings\%USERNAME%' hardcoded, rather than '%USERPROFILE%'. So half of your programs point to the D:, half to the C: .

Another choice would be to mount a separate partition to C:\Documents and Settings, just like you mount /home. But, under Windows you can't mount a drive in a directory unless that directory doesn't already exist (under Linux the directory can exist, but must be empty). So next step would be delete the Documents and Settings directory, yeah? Well you're never allowed to do this under Windows. Even if you could somehow remove all the open file/folder locks on it, Windows says that Documents and Settings is an important folder and you're not to touch it.

So, once again and with feeling, I love Linux.

---

### Post by Footer on 2005-10-12
[QUOTE=aysiu]It's easy. You ```
sudo kwrite /etc/apt/sources.list
``` Do a find/replace on the word *hoary* for *breezy*, save the file, then type this in the terminal ```
sudo apt-get update
sudo apt-get dist-upgrade
```[/QUOTE]

This is exactly what I did and I'm still running strong today (Wednesday).  Tomorrow (?) is the official release?

Linux (ubuntu/kubuntu) is GOOD STUFF.

:)

---

### Post by ltmon on 2005-10-12
[QUOTE=Takis]Yeah but how many programs have 'C:\Documents and Settings\%USERNAME%' hardcoded, rather than '%USERPROFILE%'. So half of your programs point to the D:, half to the C: .

Another choice would be to mount a separate partition to C:\Documents and Settings, just like you mount /home. But, under Windows you can't mount a drive in a directory unless that directory doesn't already exist (under Linux the directory can exist, but must be empty). So next step would be delete the Documents and Settings directory, yeah? Well you're never allowed to do this under Windows. Even if you could somehow remove all the open file/folder locks on it, Windows says that Documents and Settings is an important folder and you're not to touch it.

So, once again and with feeling, I love Linux.[/QUOTE]

Thanks for the clarification.  I always thought somehow that linking the filesystem structure to the partition table in this way was a screwy idea -- this is just one of the good reasons why.

L.

---

### Post by hlfrk414 on 2005-10-12
How important is it to upgrade to Breezy? I just got all the proprietary crap ( wireless PCMCIA and Laptop battery measurment) working and I'm afraid to upgrade with everything I've messed around with. I realize that  a rollback is a viable option, unlike in windows, but what improvements are there? Is the control center in KDE more stable now? Is breezy required for Open Office 2? Because that's the only motovation I'm seeing for me.

---

### Post by jnev on 2005-10-13
[QUOTE=hlfrk414]How important is it to upgrade to Breezy? I just got all the proprietary crap ( wireless PCMCIA and Laptop battery measurment) working and I'm afraid to upgrade with everything I've messed around with. I realize that  a rollback is a viable option, unlike in windows, but what improvements are there? Is the control center in KDE more stable now? Is breezy required for Open Office 2? Because that's the only motovation I'm seeing for me.[/QUOTE]

same with me. i have all my stuff configured finally so i'm kinda scared to dist-upgrade. can anybody console me?

---

