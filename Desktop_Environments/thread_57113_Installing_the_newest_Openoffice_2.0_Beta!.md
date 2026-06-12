---
title: "Installing the newest Openoffice 2.0 Beta!"
date: 2005-08-15
forum: Desktop Environments
---

### Post by daller on 2005-08-15
Hi there,

On this ftp-server, i've found some debian install-files (.deb) for Openoffice 1.9.122 (Well .123 is the newest):

[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)

I Downloaded them, and ran "dpkg -i *.deb". (within the extracted folder - of course!)

My 1.9.82-installation, is now replaced by 1.9.122!

Now Openoffice will not start!

Running "soffice" normally start openoffice. Now it doesn't!

...has the package been renamed lately?

Well, I solved it by downgrading to 1.9.82 again - But its buggy - Please help me!

---

### Post by tonysathre on 2005-08-15
this might not be exactly accurate, but i think you need to unistall the old version first

---

### Post by almarag on 2005-08-15
Rats!!, I've found this URL too late!!!!. :) Well, doesn't matter, I just installed from another source, with some workarounds, but this stuff really works well... 

In response, you MUST uninstall the old openoffice packages first. If you don't do that, you installation will be broken.

Thanks for the URL. I'll check that packages in home.

almarag.

---

### Post by daller on 2005-08-16
Well, how do I uninstall the packages?

Can i be accomplished without using "apt-get remove" on each package?

---

### Post by tonysathre on 2005-08-16
use synaptic and seach for openoffice, it will automatically select all the packages that need to be removed when you click openoffice and remove, then you should be able to reinstall the new version with synaptic with no problems

---

### Post by daller on 2005-08-16
After uninstalling the packages, the installation with "dpkg -i *" (within the directory), still upgrades from 1.9.82 to 1.9.123 - So somehow the 1.9.82-version is not uninstalled?

Is there a repository, where a newer openoffice version is available? (newer than 1.9.82) ???

---

### Post by tonysathre on 2005-08-16
did u do a "complete removal" with synaptic?

---

### Post by daller on 2005-08-17
With "complete removal" - you mean the "--purge" feature of apt-get?

I tried a complete removal - but it didn't seem to solve the problem...

...An installation of the 1.9.123 still doesn't work...

Is there a repository where a newer version is available? (just newer than 1.9.82 plz!)

...If not - where did you download your .deb-files for openoffice 2.0 Beta?

---

### Post by tonysathre on 2005-08-17
search your system for the openoffice directory and delete the contents, i think its in the /usr/lib/openoffice directory or /usr/local/openoffice, i dont remember for sure, where ever it is delete the contents

---

### Post by daller on 2005-08-17
Well, I also have Openoffice.org 1.1 installed - And i don't want to mess it up!

Is there no way to install it from a repository? (it works almost every time!)

...At last - .123 is experimental, right? - Have anyone of you got it working?

---

### Post by Locomorto on 2005-08-18
I installed it from there, but it did not add entries into the K-Menu and it did not properly chmod some files. After i manually went through and fixed this I can use it like normal. Perhpas if you tried using the debian experminental repositories? They did have m122 in there last time i was on them.

---

### Post by rykel on 2005-08-23
Looking at all the troubles we Linux people have to go through just to install the latest OpenOffice.org makes me wonder why nobody in OOo team bothers to just make an [autopackage](http://www.autopackage.org) for us to download?

***One OpenOffice.org autopackage-does-it-all.***

Or at least offer it in addition to a DEB.

---

