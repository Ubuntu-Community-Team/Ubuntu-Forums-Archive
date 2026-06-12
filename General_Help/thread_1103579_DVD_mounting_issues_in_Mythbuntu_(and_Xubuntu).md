---
title: "DVD mounting issues in Mythbuntu (and Xubuntu)"
date: 2009-03-22
forum: General Help
---

### Post by Zeedok on 2009-03-22
I have just received a new Mythbuntu system which I am trying to whip into shape.  I have a few little irritations, one if them involves the DVD drive.

My system:


> Antec Micro Fusion 350 HTPC Case
Intel Core 2 Duo E8400 CPU 3.0 GHz
Gigabyte GA-EG41M-S2H Mainboard
4GB DDR2 PC6400 (2x2GB) Dual Channel RAM
8X Dual Layer DVD+RW + 20X DVD+-RW + CD-RW Combo Drive
1TB 7200RPM SATA HDD
512MB NVIDIA Geforce 8400GS
Gigabit Ethernet
Hauppauge Nova-T-500 MCE Dual DVBT SD/HD tuner
Cordless Keyboard & Optical Mouse
Mythbuntu 8.10 with Xubuntu desktop

When I insert a DVD it is not mounting correctly.  If I mount the drive manually (or by using Mountmanager - which I found in the repos) I can then play it (I have all the codecs etc, so that is not an issue).  At other times I can't seem to mount the drive properly (I'm sure it is a permission problem), but if I reboot with the disc in the drive, then it mounts and I can play it in VLC or in Mythbuntu itself.

My current FSTAB line looks like this:

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

Which I copied from my laptop (where the DVD drive behaves correctly - ie when I enter a DVD data disk it pops up ready to read the files, or when I enter a video DVD it asks me whether I want to open the disk with Totem).

What am I missing - is there an error in my FSTAB?  Is there another config file that I need to check/edit?  Could it be a installation issue (eg a cable selection on the drive itself - I only have one drive)?

Thanks in advance for any suggestions and help.

---

### Post by Zeedok on 2009-03-22
Bump.

---

### Post by Zeedok on 2009-03-22
Bump

---

### Post by Zeedok on 2009-03-23
Bump.

---

### Post by Zeedok on 2009-03-23
Someone on another forum site has suggested checking the privileges of my user (ie System -> Administration -> Users and Groups -> Properties of my user and making sure that the "Use CD-ROM" box is checked).

Has anyone else had this problem before? Surely most distros would have that set-up when you establish a new user?? I'll try deleting the entry in the fstab to see if that helps.

Could I have inadvertently changed this somehow?  What are the defaults for a clean Mythbuntu install?

---

