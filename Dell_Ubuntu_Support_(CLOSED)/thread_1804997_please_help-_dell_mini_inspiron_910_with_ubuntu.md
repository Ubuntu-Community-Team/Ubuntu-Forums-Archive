---
title: "please help- dell mini inspiron 910 with ubuntu"
date: 2011-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ncb9294 on 2011-07-15
hi all, I really need your help
recently, after I logged onto my dell mini inspiron, the web browser (ubuntu) stopped recording my history, and wouldnt let me refresh or go back pages.  Now, I cant even get on.  Once I turn the  computer on, I get an alert which says "your home directory is listed as '/home/(my name)' but it does not appear to exist.  Do you want to log in with the /(root) directory as your home directory? it is unlikely anything will work unless you use a failsafe session."  Then, whichever I press(yes or no) it brings me into a log in page I have never seen before and I dont have a password.  can anyone please please help me it is so important that I get onto my computer, I have all of my college stuff saved on it. thank you

---

### Post by snowpine on 2011-07-15
Welcome to the forums! Sorry to hear about your troubles.

Before you do anything else, you should recover your important files from the computer. The easiest way to do this is to boot with an Ubuntu Live CD or Live USB and copy your files to an external drive.

Here are easy instructions for creating a Live CD/USB:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Follow up to Step 3: Try It! to boot Ubuntu in "live" mode and rescue your coursework. :)

---

### Post by ajgreeny on 2011-07-15
While you are running the live CD/USB, mount the hard disk partition that should contain your home folder, and check that the files are still there.  You will need to do that to backup your home so that will be the first step.

Have you carried out any activities on your separate /home partition, if you have one, as that may have changed the UUID and therefore given problems with mounting it at boot time.  To check that possibility lets see the /etc/fstab file from your installed ubuntu with command ```
cat /media/*disk*/etc/fstab
```where disk is the partition name for the installed ubuntu, as we do not want the fstab of the live disk.

Finally show the output of ```
sudo blkid
sudo fdisk -l
```

---

