---
title: "SoftRAID and LVM - how is it started"
date: 2009-05-02
forum: General Help
---

### Post by mynd2 on 2009-05-02
Hi there !  

I have a question.  I've set up soft RAID1 and LVM over it (ubuntu 9.04). 
Everything works. But I cannot get an understanding of several things: 

1. Is it right that soft raid is started with  mdadm --auto-detect or mdadm --assemble --scan which are the same ? 

2. WHERE are these commands in system ?
init.d/mdadm runs monitor only and doesn't start RAID (I've checked)
So how does it know what should be brought up and when ?

3. And the most mysterious.
I run:
vgchange -an - LVM deactivated
mdadm --stop ... - RAID is down 
mdadm --assemble --scan - RAID is up and LVM is UP TOO.
How does it know about RAID start ?
Where is the script ?
How does it work together ????

Would appreciate any clarification. Thanks
Alex

---

### Post by fjgaude on 2009-05-03
I don't know anything about LVM, but **mdadm** raid, yes.

When an array is first created mdadm creates a UUID in the superblock in each drive of the array. The kernel knows of this and auto assembles the array on bootup, but doesn't mount unless the command line is in the **/etc/fstab** file.

Some info is in the /etc/mdadm/mdadm.conf file but is really only used in complex setups. The UUID there should match the UUID you find for each drive. This is not the UUID that mounts a single drive.

Take a look at **man mdadm** pages for the whole story. A good link:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

Hope this helps.

---

