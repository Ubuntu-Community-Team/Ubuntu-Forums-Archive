---
title: "CD Drive isn't being auto mounted anymore"
date: 2006-06-26
forum: Desktop Environments
---

### Post by shawnrgr on 2006-06-26
My cd drive isn't being auto mounted anymore. Before the upgrade from 5 to 6 the cd drive would be auto mounted when i put on in the drive and would apear in "My Computer" now there is an icon in "My Computer" that says "CD-RW/DVD-ROM Drive" but when I put a cd in the drive it doesn't do anything. In a more step by step detail....


open my computer
i can see cd/dvd drive icon
insert cd
cd spins
stops spinning
no changes
no cd icon auto placed on desktop either
double-click on cd icon in my computer and cd spins
still nothing
double-click on icon again and i get: 
     Unable to mount the selected volume.
     mount: block device /dev/hdc is write-protected, mounting read-only
     mount: /dev/hdc already mounted or /media/cdrom0 busy
     mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0
i goto /media/cdrom0
cd is mounted and i can access it from their. but thats not what i want.

When I plug in my external hd, a usb hd icon is displayed on the desktop after it was auto mounted. How can i fix this so the cd works like my usb hd.? ](*,)

---

### Post by shawnrgr on 2006-06-27
anyone?

---

### Post by michux on 2006-06-27
[QUOTE=shawnrgr]My cd drive isn't being auto mounted anymore. Before the upgrade from 5 to 6 the cd drive would be auto mounted when i put on in the drive and would apear in "My Computer" now there is an icon in "My Computer" that says "CD-RW/DVD-ROM Drive" but when I put a cd in the drive it doesn't do anything. In a more step by step detail....
[/QUOTE]

You can try an experiment - before logging in graphically, login in console (CTRL+ALT+F1) and go to your /home folder and move your personal home to another place, like:
$ cd /home
$ sudo mv yourname yourname.backup

And then switch to the GUI (CRTL+ALT+F7) and login to Gnome. See if your CD is mounted now. If so, it means there is some problem with your personal configuration after the upgrade. If it still doesn't work, there's a general problem with your system. Let us know what is the result and we'll try to figure out what next.

Of course after the experiment you can remove the new /home/yourname and move the backup home back to the original place to be able to access your files in Gnome.

---

### Post by shawnrgr on 2006-06-27
well i logged in as root, which i've neer done so all the settings were default still, and the cd drive still didn't auto mount. ;(

---

### Post by michux on 2006-06-27
[QUOTE=shawnrgr]well i logged in as root, which i've neer done so all the settings were default still, and the cd drive still didn't auto mount. ;([/QUOTE]

Did you check the logs? Any information? Do you have hotplug or HAL/udev activated?

---

### Post by shawnrgr on 2006-06-27
which logs should i check? i looked in the /var/sys log and nothing was posted.

---

### Post by chrestomanci on 2006-06-28
I have been having similar problems, and found [this thread]("http://www.ubuntuforums.org/showthread.php?p=1173208") that discusses the issue.

---

### Post by shawnrgr on 2006-07-10
problem fixed after reinstall.

---

