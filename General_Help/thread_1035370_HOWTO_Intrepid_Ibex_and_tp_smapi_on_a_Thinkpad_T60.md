---
title: "HOWTO: Intrepid Ibex and tp_smapi on a Thinkpad T60"
date: 2009-01-09
forum: General Help
---

### Post by jsroth on 2009-01-09
Hi, 

I had some issues installing the tp_smapi module in an appropiate way, therefore I just want to let everybody know how it worked for me with Ubuntu 8.10 Intrepid Ibex and a Thinkpad T60

Although I read everywhere that the tp_smapi module is shipped within ubuntu i couldn't find it. Therefore I had to install the sources via
```
sudo apt-get install tp-smapi-source
```
and of course we need these packages
```
sudo apt-get install build-essential linux-source-'uname -r'
```

Then change to /usr/src/ and unpack the two downloaded files (one should be the linux-sources and one should be the tp-smapi-source file).
Now change into the tp-smapi-source directory and do a make install with HDAPS=1 if you want to load HDAPS or just leave if you want to ignore it.
But since this is giving you this error:
```
Makefile:31: *** This driver requires kernel 2.6.19 or newer, and matching kernel sources. You may need to override KVER= or KSRC=/usr/src/tp-smapi or KBUILD=/usr/src/tp-smapi or MOD_DIR=/lib/modules//kernel.  Stop.
```
You'll have to change the make command a little bit
```
sudo make install HDAPS=1 KSRC=/usr/src/linux-headers-'uname-r' 
```

Now the tp_smapi module should be installed without any further problems.

If you want to make permanent changes to, e.g. your charge-thresholds do
```
sudo apt-get install sysfsutils
```

Then edit the /etc/sysfs.conf by adding the following lines:
```
devices/platform/smapi/BAT0/start_charge_thresh=81
devices/platform/smapi/BAT0/stop_charge_thresh=85
devices/platform/smapi/BAT0/inhibit_charge_minutes=15
```

Then your Thinkpad should be working fine with tp-smapi under Ubuntu. Enjoy!

Thanks to mbsullivan and tastatur who have a lot of this done in [this thread](http://ubuntuforums.org/showthread.php?t=546537&page=2).

---

### Post by civetta on 2009-05-04
Would this work (and be beneficial) with the T500 under Jaunty?

---

