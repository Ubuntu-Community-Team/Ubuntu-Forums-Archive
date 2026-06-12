---
title: "X11 doesn't start"
date: 2006-08-22
forum: Desktop Environments
---

### Post by barna on 2006-08-22
Hi,
I was stupid enough to make the latest X11 update (instead of happily using a system which was finally working...)

Now X does not start. Logfile is attached. 
I have checked that the files /etc/X11/xorg.conf and /usr/bin/X have not changed during the update. 

Any idea?
I am using a Toshiba Satellite A60, with the kernel 2.6.15-23 (because with the more recent kernels of ubuntu my wireless card does not work)

Thanks
Daniel

---

### Post by ohgod on 2006-08-22
have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=241254]("http://www.ubuntuforums.org/showthread.php?t=241254")

---

### Post by barna on 2006-08-23
Hi,
Thanks for redirecting me to the appropriate thread. 
I am hesitating to run that bugfix, being afraid of further problems (especially due to the comment
"If you installed the proprietary drivers for ATI or Nvidia cards you will have to reinstall them otherwise they won't work")

Anyway, I had a LOT of problems before with any linux distros on my notebook, so I was careful enough to install ubuntu to another partition as well, and I keep this working version without any changes or updates. 
I checked which files are affected in this xserver-update. These are the following: 
In the /usr/bin/ directory: gtf  ioport  pcitweak  scanpci  Xorg
And everything below /usr/lib/xorg/modules/
So I simply overwrote these files with the old ones from my 'safe' installation, and now everything seems to work. I think I will leave everything in this state, and make no updates in the future. 

If anybody has problems with the bugfix, I can send these files.

Daniel

---

