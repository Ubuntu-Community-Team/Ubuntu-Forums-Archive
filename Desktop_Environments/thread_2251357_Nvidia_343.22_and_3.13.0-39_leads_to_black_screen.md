---
title: "Nvidia 343.22 and 3.13.0-39 leads to black screen"
date: 2014-11-03
forum: Desktop Environments
---

### Post by dannyboy79 on 2014-11-03
I'm running Xubuntu 14.04.1 and I have a very weird situation, for some reason I can't get lightdm or my desktop to work using the Nvidia 343.22 driver from the website. I've never had issues with it in the past up until yesterday when I was trying to install either kernel 3.16 or 3.17 from the Utopic Mainline kernel branch. Basically after I installed the kernels i thought I needed to reinstall the nvidia driver but during it's install it failed due to finding a gcc mismatch. Meaning the kernel was compiled with gcc-4.6 but my system has gcc-4.8 on it so I aborted the install of the nvidia driver, removed the extra kernels that I installed, reinstalled the nvidia driver and now when I try to boot into kernel 3.13.0-39-generic all i get is a black screen. The monitor is receiving a signal because the monitor light remains on and I can get to tty1 and see text just fine.
Here's the Xorg.0.log file  [http://paste.ubuntu.com/8808970](http://paste.ubuntu.com/8808970)

The weird entries are the 2 last lines being
```
NVIDIA(GPU-0): Deleting GPU-0
[     9.826] (EE) Server terminated successfully (0). Closing log file.
```

Here's my .xsession-errors file   [http://paste.ubuntu.com/8809074](http://paste.ubuntu.com/8809074)

Here's the xorg.conf that sudo nvidia-xconfig generated  [http://paste.ubuntu.com/8809115](http://paste.ubuntu.com/8809115)

i've even tried disconnected my second monitor but that still doesn't solve anything, i've even tried swapping out which monitor is connected to the gpu, i still only get a black screen. there's no blinking cursor on it either, it's just a black screen and like i said the monitor light is on, which means that it's rceiving some signal and again, tty1 does work.

I can remove the nvidia driver and get the open source driver to work but i want to use 343.22 as the driver available thru Additional Drivers is only 331.38 and that's like 11 months old. I don't want to enable the xorg-edgers ppa either. I want to get this 343.22 driver to work. I want to figure out what's preventing the X Server from terminating as per what the log shows. Any assistance with this would be much appreciated. I'm very familiar with Ubuntu, i've been using it since Breezy Badger days and i'm not afraid to work from the terminal (tty1). If anyone has any suggestions of where to look to solve this please point me in the right direction. If you're merely going to say that Ubuntu doesn't support the use of the Nvidia website drivers than please just save your breath. I'm looking for someone to help me get the nvidia driver 343.22 working. Thank you very much!

---

### Post by dannyboy79 on 2014-11-10
i realized that I could startx from tty1 but not sudo service lightdm start from tty1.  i found some very useful info within the lightdm log file located in /var/log/. It was attempting to run a script that wasn't there in my home directory. 

during all the trouble shooting i thought restoring a / (root partition) backup i had just recently made using clonezilla would fix everything. it was a backup of the / partition only. once that restored i thought life would be good BUT the way i had my partition scheme setup it was a gigantic failure because that only restored / and NOT /var/, the 2 became out of sync. meaning the package manager didn't know what packages were installed and which weren't and after hours of trying to fix my system i realized that backing up my home folder and copying a few config files like /etc/fstab I had enough and just did a fresh install completely reformatting my / and this time I didn't make /var/ a separate partition that way when I use clonezilla to make an image of my / partition it will be a complete system i can restore if i need to ever.

so sadly i never figured out why i couldn't get past a black screen but everything is working now. that xubuntu install was an upgrade from 13.10 and had many years of config files in /home/ which could've been making my life harder. i renamed my old home directory and created the same user and mounted the same partition to /home/ so that in my new system i had /home/ubu and /home/ubu_old and for any program i install that has a lot of config I just go into my old home and copy/paste it's relavent config file and paste it into my new home. i obviously also copied over my steam library from my old home to my new home. it's important to note that there could be something in my old home that was preventing my system from booting correctly so it's not always best to reuse home but do what i did where you rename your old home, create the same user again cause that way you'll get a fresh home directory.

---

### Post by pqwoerituytrueiwoq on 2014-11-10
did you install via the .run file from nvidia?
i am using the 340.56 driver with the 3.16.6 mainline kernel, (3.17 and 3.18 will not work with 14.04's virtualbox)
i got the drive from the xorg edgers ppa

looks like it is not seeing your monitor and is during the display off

i managed to solve the gcc error, but it just game me a new one
if you want a newer kernel i think you need to use the xorg edgers ppa, unless you want to use nouveau

---

