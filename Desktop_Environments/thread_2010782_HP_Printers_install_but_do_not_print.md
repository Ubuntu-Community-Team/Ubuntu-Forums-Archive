---
title: "HP Printers install but do not print"
date: 2012-06-26
forum: Desktop Environments
---

### Post by Billpage on 2012-06-26
Hi everyone.
I have just installed Lubuntu 12.04. It correctly identifies and installs my two HP printers (Laserjet 1018 and PSC 1200) but when I try to print to either, it appears to do so but nothing happens at the printer. Print manager shows that job/s are either completed or stopped!

What am I doing wrong? Ubuntu 11.10 were completely seamless.

---

### Post by Guilden_NL on 2012-06-26
I use HPLIP, the latest version is working perfectly.

[http://hplipopensource.com/hplip-web/downloads.html]("http://hplipopensource.com/hplip-web/downloads.html")

---

### Post by VanillaMozilla on 2012-06-27
You might try hplip-gui too.  There are so many frikkin confusing places to view printer settings, and so many reasons it might not work.  Poke around the tabs of the HP Device Manager.  Some of those are helpful.  Also the printer Web page.

You might find you've got it in a knot and it's not accepting jobs or something.  There are so many things you can do wrong, and that presents most of the info for you in more or less one place.

---

### Post by Rex Bouwense on 2012-06-27
I just installed the latest version of HPLIP.  Recommend you do also.  Make sure that you uninstall the old version so there are no old settings to screw up the new install.

---

### Post by Huszarnyi on 2012-08-14
I also had this issue. Fixed it with downloading the latest HPLIP. I advise you to do the same. :)

---

### Post by Savio2010 on 2012-08-14
First install hplip
Second run hp-diagnose_plugin using sudo


```
sudo apt-get install hplip
sleep 5
sudo  hp-diagnose_plugin
```Running hp-di.... with sudo privileges is important because it does not ask for a password during installation and fails.
Download and install the plugin

Hope it helps.. It worked or me:popcorn:

---

