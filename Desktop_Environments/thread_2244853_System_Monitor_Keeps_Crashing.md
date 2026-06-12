---
title: "System Monitor Keeps Crashing"
date: 2014-09-19
forum: Desktop Environments
---

### Post by brendonwp on 2014-09-19
I have a clean install of Ubuntu 14.04 on a Core2 Duo 2.97GHz desktop with 8GB of RAM.  Ubuntu is installed on a 128GB SSD and dual-boots with Win8, with data on 2 x 1TB Western Digital HDDs.  Home partition and /tmp on one HDD (ext4), and two NTFS partitions on the other HDD for Win 8.  I use Ubuntu mostly.

I need to share data between OSs, so the one NTFS partition is mounted under /media/datashare in Ubuntu so I can sync to Dropbox and Google Drive whenever I boot Ubuntu.  System monitor keeps crashing under Ubuntu which makes me worry that I have underlying problems.  I was running 12.04 for years and never had system monitor crash on me.  

Had to monkey with file permissions on NTFS to get ownership of the NTFS partition, and upset Win8 in the process. Don't think this is related.     

Will attach the crash report for system monitor when it happens again.

---

### Post by brendonwp on 2014-09-22
I changed my video drivers from open source to Nvidia proprietary, and haven't had system problems for a couple of days

---

### Post by post-y on 2014-09-22
Just out of curiosity, how on earth did you install Nvidia proprietary driver? When I installed it, everything graphical (X11) crashed beyond repair, and I had to reinstall my whole system again.

---

### Post by brendonwp on 2015-01-27
Haven't looked at this thread for ages - if you happen to be following this still, I did:

sudo apt-get install nvidia-331 #installs proprietary drivers for nVidia cards

Then went to the dashboard and started the Additional Drivers application.  On the tab that comes up I selected the radio button for "Nvidia binary driver".

That did it.  It isn't the very latest nVidia driver, but is good enough for me.

---

