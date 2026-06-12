---
title: "How to scan from printer in Ubuntu"
date: 2009-06-11
forum: General Help
---

### Post by luke0927 on 2009-06-11
OK so i succesfully installed my HP J6480 printer in ubuntu.  It is a network printer and the j6400 driver was already in ubuntu.  would this driver install the feature to scan and fax?  With windows you just install the CD how do i set up scanning and faxing.  

thanks!

---

### Post by crossedout on 2009-06-11
Hi there,

I had the same problem with my samsung.  I found out that in order to get network scan going, xsane was needed.  Turns out my samsung is not supported by sane so I am out of luck.

You can check the supported devices page [[COLOR="Blue"]here[/COLOR]]("http://www.sane-project.org/sane-mfgs.html#SCANNERS").

I took a quick scan and did not see your hp listed but maybe I overlooked it as I was looking rather quickly.

Other than that, it is up to the manufacturer to make a driver that supports all platforms.  Additionally, you should do some extensive searching, there may be some workaround floating out there for your specific hp.

Good Luck,
-Xout

---

### Post by Tamlynmac on 2009-06-11
You need to install the newest HP driver.

Go to this link and follow the directions for the automatic install (make sure you read the Instructions for using the [Automatic Installer]("http://hplipopensource.com/hplip-web/install/install/index.html").)

[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

I already checked your printer in the supported printers section and after installing the new driver your printer should automatically be capable of scanning with Sane.

Good Luck & Hope this helps.

---

