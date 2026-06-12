---
title: "Three problems in Hoary"
date: 2005-07-25
forum: Desktop Environments
---

### Post by Aijaz Akhtar on 2005-07-25
1. I could not make my Win partitions readbl;e in Ubuntu. This is my revised etc/fstab file. This was the setting when I had Mandrake, in Ubuntu, I am not very sure about asignment of hdaX naming in Ubuntu. However, this is my edited etrc/fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda2       /mnt/Win-C      vfat    defaults       0 0 0 0   0 0
/dev/hda6       /mnt/Win-E      vfat    defaults       0 0 0 0   0 0
/dev/hda7       /mnt/Win-F      ntfs    defaults       0 0 0 0   0 0
this 0 0 0 0  0 0 part has worked in many other distros, but do I have to add -ro?
And since Windows recognise my USB Flash drive (pendrive as it is some times called here and labelled TRAVELDRIVE) as D Drive, I have followed the Windows nomenclature here.
In many other distributions, I could make fstab work. but I have failed in Ubuntu as in some earlier cases of other distros too. (PCQ, e.g., though I could succeed in White Box, though both are Fedora) 

2. I am unable to install applications and the Syneptic manager cannot find the deb files in my USB stick (labelled TRAVELDRIVE). I could install only translation packages from Ubuntu CD. Attempted custom, adding repository, and so many things. And also apt-get that did not work.
I could log in as root in Root Shell, and there gave the command apt-get install /media/TRAVELDRIVE/xx.deb, but failed in installing. This is copied from shell:

root@ubuntu:/home/aijaz # cd /media/TRAVELDRIVE
root@ubuntu:/media/TRAVELDRIVE # apt-get install xfce_3.8.18-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xfce_3.8.18-2ubuntu1_i386.deb
root@ubuntu:/media/TRAVELDRIVE #
In syneptic too, there is no package for the windows manager that I can add. However, if I extract all files in .deb files (or even tar.gz files in case of other packages I have), and extract the files from etc folder to etc. bin folder files to bin folder, will they work?

3. After installing l10 translations for Arabic, Bengali and Hindi through syneptic where I succeeded, and reconfiguring locales (THROUGH dpkg-reconfigure locales, As I was advised in some forums) I logged in again selecting Hindi as a language, but it said 'language hi_in (or bn-In) does not exist, loading default."  How can I get my languager interfaces as are seen in the Live CD.

---

### Post by ubuntp on 2005-07-25
1. Those zeroes are completely unnecessary, 0 0 will be enough. You should add* -o ro *to the NTFS drive. Did you already mkdir the directories you want those drives mounted to?

2.apt-get doesn't work that way. If you want to install a package directly you have to use* dpkg-i package.deb*. apt-get can only install packages from a repositorie (like a CD or a server). synaptic cannot handle .deb files directly either.

---

### Post by anil_robo on 2005-12-22
Please see my how-to on Hindi and similar languages here:
[http://ubuntuforums.org/showthread.php?t=102778&highlight=hindi](http://ubuntuforums.org/showthread.php?t=102778&highlight=hindi)

---

### Post by aysiu on 2005-12-22
You'll love my signature...

---

