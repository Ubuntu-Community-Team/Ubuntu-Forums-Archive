---
title: "xsane cannot detect my HP C6180 printer/scanner"
date: 2006-12-03
forum: Desktop Environments
---

### Post by ricardo06 on 2006-12-03
Hello,
I got a nice HP photosmart C6180. It is connected to my edgy machine thru dhcp in a home network and perfectly detected for printing. (the printer uses the wifi capacity to connect to the nerwork) . Both cups and "Hp direct jet" meke the printer accessible.
But xsane does not detect it at all. As i got it specifically for scanning, i am a little frustrated.  
Thanks to anybody who can help.

Richard

edgy on AMD64

---

### Post by Sef on 2006-12-03
From what I can tell from the [sane-project]("http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=&bus=usb&v=&p="), your model is unsupported.

---

### Post by gozzerd on 2007-01-28
ricardo, 

if you haven't already gotten it taken care of, go here:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

they have an installer for downloading and installing hplip so that it will do most of the stuff, including scanning to a file and scanning to email. xsane functions with their toolbox program. When I installed from the ubuntu repositories it didn't work.  

For me, the installer worked well.  Who knows what will happen when it's time to upgrade to feisty. 

gozzerd

---

### Post by ricardo06 on 2007-01-29
Gozzerd,
Thanks a lot for this info. I found this reference when i was striving to install. It worked allright. I don't know what will happen for the next upgrade. The upgrade to edgy was a nightmare for me. 
Richard

---

### Post by paulcalabro on 2007-02-17
> **gozzerd said:**
> ricardo, 

if you haven't already gotten it taken care of, go here:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

they have an installer for downloading and installing hplip so that it will do most of the stuff, including scanning to a file and scanning to email. xsane functions with their toolbox program. When I installed from the ubuntu repositories it didn't work.  

For me, the installer worked well.  Who knows what will happen when it's time to upgrade to feisty. 

gozzerd


[SIZE="6"]This worked the trick for me as well........[/SIZE] :)

---

### Post by anguste on 2007-02-18
Try sometimes "hpoj", that's fantastic and now officially supported by HP

---

