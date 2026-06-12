---
title: "Update problems with RKWard"
date: 2008-04-21
forum: Education &amp; Science
---

### Post by Unstuck on 2008-04-21
I am trying to use RKWard for an econometrics paper but am having trouble uploading .odt (OpenOffice Calc) files and upgrading plugins--the two seem to be related.

When I try to load my .odt file, I get a long message that looks something like > The R-backend has reported one or more error(s) while processing the '/usr/share/apps/rkward/00saveload/import/import_csv.xml'.  This may lead to an incorrect output and is likely due to a bug in the plugin.  A transcript of the error messages is shown below: Error in type.convert(data[[i]], as.is = as.is[i], dec = dec, na.strings = character(0)) : invalid multibyte string so I tried to update the plugins and got this message > The directory you are trying to install to (/usr/local/lib/R/site-library) is not writable with your current user permissions. If you are the adminitstrator of this machine, you can try to install the packages as root (you'll be prompted for the root password). Otherwise you'll have to chose a different library location to install to (if none are writable, you will probably want to use the "Configure Repositories"-button to set up a writable directory to install packages to). so then I click on the button that says something similar “Log in as root” and nothing happens.  

I'm not really sure what to do, but I would love to get this program working for me.

---

### Post by earlycj5 on 2008-04-22
> **Unstuck said:**
> I am trying to use RKWard for an econometrics paper but am having trouble uploading .odt (OpenOffice Calc) files and upgrading plugins--the two seem to be related.

When I try to load my .odt file, I get a long message that looks something like  so I tried to update the plugins and got this message  so then I click on the button that says something similar &#8220;Log in as root&#8221; and nothing happens.  

I'm not really sure what to do, but I would love to get this program working for me.

Easiest thing I've done is to run RKWard as root(% sudo rkward) and then update.

---

### Post by Unstuck on 2008-04-23
I opened the program as suggested above and now get the following output when the packages fail to update.
> > options (repos=c (CRAN="http://rh-mirror.linux.iastate.edu/CRAN"))
> install.packages (pkgs=c ("boot", "cluster", "KernSmooth", "lattice", "mgcv", "nlme", "rcompgen", "rpart", "survival", "VR"), lib="/usr/lib/R/library", destdir="/home/derek/.rkward/package_archive")
Error in download.packages(p0, destdir = tmpd, available = available,  : 
	'destdir' is not a directory
Execution halted

I have no idea what this means...

---

