---
title: "How to: Copy Live CD and make it bootable?"
date: 2009-05-19
forum: General Help
---

### Post by pgmer6809 on 2009-05-19
I have a live CD of gparted_03. It is an ISO image (mount cmd shows it mounted as filetype ISO9660)
If I try to copy it with brasero, brasero reads the files  OK and then ejects and asks for a blank to be inserted but then it wont recognize the blank media in my drive.

So I copied the contents to my home directory and then using right-clik copied the results to a blank CD.
Files end up there OK, but the result is not bootable.

I also tried making an ISO image first using genisofs and then using right clik to burn the cd.
Again the CD is OK, it can be mounted and the files are there, but it wont boot. 
The iso image can also be mounted with the -o loop option and it looks OK.

finally I tried wodim but wodim -scanbus and wodim --devices just give me errors that it cannot find the SCSI driver.

FYI the original CD looks like:

/boot         (has various files in this directory)
/selinux      (has various files in this directory)
gparted_03.dat (one big 44MB file)

and it boots fine on several different computers.

Any suggestions?
Thanks, 
pgmer6809

---

### Post by Concrete on 2009-05-19
> **pgmer6809 said:**
> So I copied the contents to my home directory and then using right-clik copied the results to a blank CD.
Files end up there OK, but the result is not bootable.

This is the problem.

.ISO formats are actualy, archiving format in same time they can be bootable to. When u extract the .ISO then will become just dir of source of ISO image.

If u wont it bootable u must burn it like ISO.

---

### Post by pgmer6809 on 2009-05-20
> **Concrete said:**
> This is the problem.

.ISO formats are actualy, archiving format in same time they can be bootable to. When u extract the .ISO then will become just dir of source of ISO image.

If u wont it bootable u must burn it like ISO.

OK, I thought of that. If you check the rest of the post u will see that I used genisofs to make the directories into an iso image.
I then burned that iso image to a CD. It is not bootable either.

e.g.
```
 ls -R Gparted-LiveCD/
```
Gparted-LiveCD/:
boot  gparted.dat  syslinux

Gparted-LiveCD/boot:
boot.cat  gparted  gparted.igz  grub  help.msg  memtest86

Gparted-LiveCD/boot/grub:
clonezilla.lst  fat_stage1_5  Gsplash.xpm.gz    jfs_stage1_5    reiserfs_stage1_5  stage2_eltorito  xfs_stage1_5
Csplash.xpm.gz  ffs_stage1_5  help.msg          menu.lst        stage1             ufs2_stage1_5
e2fs_stage1_5   grub.conf     iso9660_stage1_5  minix_stage1_5  stage2             vstafs_stage1_5

Gparted-LiveCD/syslinux:
boot.msg  options.msg  splash.lss  syslinux.cfg

```
genisofs -o gparted-livecd.iso Gparted-LiveCD
```

then burn gparted-livecd.iso to cd.

---

