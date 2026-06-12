---
title: "I have Ejected DVD RW :)"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Zmija on 2006-08-18
Please help me...  ( again :) )

Today I Eject DVD RW... And now i can enter to DVD only with /media/cdrom0/ Because I don't have Icon on my desktop when i insert DVD/CD ? How can I repair that problem?

---

### Post by ciscosurfer on 2006-08-18
Go to: System > Preferences > Removable Drives and Media

---

### Post by Zmija on 2006-08-18
Didn't help...

Something else?

---

### Post by Zmija on 2006-08-19
bump?

---

### Post by ciscosurfer on 2006-08-19
I take it you are using the Hoary version of Ubuntu b/c of where you posted...but no matter, this fix should do the trick:  edit your fstab to include your cdrom device file and mount it to /media/cdrom0 like so```
sudo gedit /etc/fstab
```And add or modify the following line to your fstab file```
/dev/cdrom /media/cdrom auto ro,noauto,user,exec 0 0
```For futher reference, please check out the following page [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Hope that helps ;)

---

