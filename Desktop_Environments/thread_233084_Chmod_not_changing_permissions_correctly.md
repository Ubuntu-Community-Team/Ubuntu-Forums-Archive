---
title: "Chmod not changing permissions correctly"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Skia_42 on 2006-08-09
I was recently trying to speed up my computer by tweaking my ex3 filesytem and I broke my graphics interface. I worked backwards and I undid all but one of the steps that I did. I edited the /etc/fstab root mount line and I cannot change it back. I tried this in the terminal:
> 
sudo -s
cd /etc
chmod o+w fstab
chmod: changing permissions of 'fstab': Read-only file System
chmod 777 fstab
chmod: changing permissions of 'fstab': Read-only file System

How do I change the permissions of /etc/fstab in order to edit the file?

---

### Post by aysiu on 2006-08-09
It sounds as if the filesystem itself (not the file) is mounted as read-only.

Read more [here](http://ubuntuforums.org/archive/index.php/t-23460.html).

You may have to use a live CD to fix this problem.

---

### Post by mlind on 2006-08-09
You root (/) is probably mounted as read-only and that's why you can't change   the permissions. Did some error happen that made it remount as read-only? Look at **dmesg** output.

---

### Post by Skia_42 on 2006-08-09
> **aysiu said:**
> It sounds as if the filesystem itself (not the file) is mounted as read-only.

Read more [here](http://ubuntuforums.org/archive/index.php/t-23460.html).

You may have to use a live CD to fix this problem.

Booting from the live cd makes sense, I had a problem with my xorg.conf file when i first got into Ubuntu.

---

### Post by Skia_42 on 2006-08-09
Okay, I was able to change the permissions of /etc/fstab by booting from my install disk (rescue mode). if I try to edit the file with nano or emacs I get this message, "Error opening Terminal: bterm". I am able to open the file with vi but I have no experience with it. I know that you can move aroudn with the "h,j,k,l" keys but I am not sure how you edit and save the text. Could anyone help me out?

---

### Post by mlind on 2006-08-09
> **Skia_42 said:**
> Okay, I was able to change the permissions of /etc/fstab by booting from my install disk (rescue mode). if I try to edit the file with nano or emacs I get this message, "Error opening Terminal: bterm". I am able to open the file with vi but I have no experience with it. I know that you can move aroudn with the "h,j,k,l" keys but I am not sure how you edit and save the text. Could anyone help me out?

I think your problem is solved when you boot back in your (persistent) Ubuntu. Root (/) should be writable again, but there's definetly a problem somewhere when kernel decided so remount it read-only.

I suggest to analyze /var/log/messages file. And schedule fsck for root partition.

---

