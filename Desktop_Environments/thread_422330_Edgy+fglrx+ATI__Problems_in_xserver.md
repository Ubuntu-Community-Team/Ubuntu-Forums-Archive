---
title: "Edgy+fglrx+ATI : Problems in xserver"
date: 2007-04-25
forum: Desktop Environments
---

### Post by gaurab on 2007-04-25
I tried installing flgrx drivers for on a machine running Edgy and couldn't configure it, following the instruction at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

The specs are:
Pentium4: 3.4GHz
RAM: 1GB
Graphics card: (by using **lspci | grep VGA**)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Problems:
1. After installing the driver I did
sudo aticonfig --initial
And when I restarted the xserver it wouldn't start anymore (error: "No screen found").

2. In the configuration file I saw double entries for Device, Monitor and Screen section and removed the older ones.
Then I got this "no device found" error.

============================
To install beryl on it I need to fix this issue, could any of you provide insight? I am posting this message after desperately searching google in vain. Saw several solution of which nothing worked (and I got either of the 2 errors)

Thanking in advance,
Gaurab

---

### Post by hagabaka on 2007-04-25
I think the double entries for Device, Monitor and Screen sections are causing the problem. I have had this happen once too after installing/configuring the fglrx package, but after I fixed it manually it didn't happen any more. To fix the problem you basically just need to remove the old Device using the "ati" driver, and Monitor and Screen sections related to that. But there might be parameters in the old sections that need to be merged into the new sections. Make a backup and try it with the old sections removed. If there are still problems, paste your xorg.conf and Xorg.0.log and people should be able to help.

---

### Post by gaurab on 2007-04-25
Thanks a lot for looking into the problem...

however as I mentioned I had already removed the older lines and still it didn't work.

I am attaching a tarball containing the 2 xorg.conf files

1. xorg.conf - the one which was there before I tried anything
2. xorg.conf.1 - the one that replaced the older xorg.conf 

As you can see the Device section had no "BusID" param, when I deleted the duplicate entries (the ones with ati), it gave me error that "no device found" and something like no BusID supplied.

So I just added the BusID part (from the old xorg.conf) to the device section. Now again it said "no device found"

May be there is a workaround but I am still clueless.

Thanks again,
Gaurab

---

