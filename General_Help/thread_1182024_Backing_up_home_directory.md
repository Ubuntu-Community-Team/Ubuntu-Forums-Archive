---
title: "Backing up home directory"
date: 2009-06-08
forum: General Help
---

### Post by DanHorniblow on 2009-06-08
Hi, I'm very new to ubuntu and I want to set my computer to automatically backup my home directory to a USB hard drive every night.

In windows i created a batch file which only backed up files that had been changed and then added that to the scheduled tasks. How do i do the same in Ubuntu?

My home directory is quite large around 80GB

---

### Post by wpshooter on 2009-06-08
Search in Synaptic for "backup" programs.

---

### Post by edm1 on 2009-06-08
Sorry i can't do much more than point you in the right direction. A common solution would be to use rsync as your backup tool (it has a gui called grsync) and cron to schedule the running of rsync.

---

### Post by RobOrr on 2009-06-08
There's a lot of backup programs in the repositories. If you're new to Ubuntu, go to Applications / Add Remove... to see the list of programs you can install from there. 

If you're interested, you could write a very lightweight python script to do the job. I use my own scripts to backup my files, which are probably not too dissimilar to your batch files. Python's also quite enjoyable to learn.

---

### Post by Therion on 2009-06-08
One of the niftiest tools out there for Ubuntu is one called **QuickStart**.  

It does all sorts of cool stuff, one of which is make quick, easy (scheduled) backups of your /Home folder, config files, etc.

Get it at the link below and be SURE you read the install instructions:

[http://quickstart.freeforums.org/quickstart-download-pics-t2.html](http://quickstart.freeforums.org/quickstart-download-pics-t2.html)

What all does it do? 
> 
1. Install the proper DVD & Codecs files so you can play a DVD in your drive using Totem, etc. (works with 7.04 / 7.10 / 8.04 /8.10 / 9.04) (32-bit / 64-bit). Please be patient on this one. Sometimes the first 2 of 6 files can take a couple minutes to finish downloading. Don't panick...

2. Back-up Your /home folders using TAR compression

3. Back-up Your / folders using TAR compression

4. Back-up Your Configuration files separately (fstab, device.map, mtab, menu.lst, and xorg.conf) using TAR compression

5. Image your Ubuntu Operating System, Master Boot Record (MBR), and Partition Table.

6. Create a Custom Scheduled (Recurring) Back-up (daily, weekly, or monthly). You decide the exact date and time

7. Create a Scheduled 1:1 Synchronized Back-Up of Selected Folders to Another Drive/Partition.

8. Restore Your System /home folders

9. Restore Your / folders

10. Restore Your configuration files

11. Install some common applications we all use with one click of your mouse. Nice when you're starting from scratch (clean install)

12. House Cleaning (delete unnecessary files throughout your computer).

13. View or Edit Your Key Files (fstab, menu.lst, and xorg.conf).

14. Back-up Your Master Boot Record (MBR).

15. Back-up Your Microsoft Windows Partition (dual booters) While in Ubuntu.

16. Format Windows Partition in NTFS with gParted.

17. Restore Your Master Boot Record (MBR).

18. Restore a Windows back-up file (image) while in Ubuntu. I've restored my entire Windows XP setup with all apps in less than 15 minutes. Nice!

19. QuickStart notifies you when updates are available. Download them with a click of the mouse.

---

### Post by SuperSonic4 on 2009-06-08
I use Back In Time: [http://backintime.le-web.org/](http://backintime.le-web.org/)

although I use the KDE interface there is a gnome one. Not sure if it's in the repos or not - it's in the KDEmod repos

---

### Post by jerrrys on 2009-06-08
**QuickStart**...excellent...thanks for the tip Therion...

---

