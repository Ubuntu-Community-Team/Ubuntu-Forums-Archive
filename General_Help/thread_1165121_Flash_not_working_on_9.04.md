---
title: "Flash not working on 9.04"
date: 2009-05-20
forum: General Help
---

### Post by iamyourdemize on 2009-05-20
I installed 9.04 two days ago and have everything working fine except flash. I have uninstalled it at least 4 times and reinstalled through the command line, through synaptic and directly from Adobe's site. Any ideas what the problem could be? I am running a 32 bit processor.

---

### Post by BZF on 2009-05-20
[SIZE=1][COLOR=Blue]there are several different verions of flash for linux, make sure ur getting the one for ubuntu[/COLOR][/SIZE]

---

### Post by clhsharky on 2009-05-20
Have you installed "ubuntu-restricted-extras"

---

### Post by baseface on 2009-05-20
just download the gzipped file and extract libflashplayer.so to ~/.mozilla/plugins

---

### Post by KhurramM on 2009-05-20
Just type and post the output of:

cat /var/lib/dpkg/status | grep flash

If u have flash components already installed, then these need to be deleted in order to use the following:

and try to install the debian package available for ubuntu from adobes website.

using:

dpkg -i file-namexxx.deb

where file-namexxx is the name of the original file u downloaded.

To: clhsharky:
> What does : ubuntu-restricted-extras has to do with flash?

---

### Post by fooman on 2009-05-20
>  			 				What does : ubuntu-restricted-extras has to do with flash? 			 		

the ubuntu-restricted-extras package includes flash.

---

### Post by t0p on 2009-05-20
> **KhurramM said:**
> 
try to install the debian package available for ubuntu from adobes website.
using:

dpkg -i file-namexxx.deb

where file-namexxx is the name of the original file u downloaded.

To: clhsharky:

What does : ubuntu-restricted-extras has to do with flash?

Okay, ubuntu-restricted-extras might be overkill if you just want to install the flash plugin.  But it is certainly the best way to make sure you have most/all proprietary codecs installed.

If you just want to install flash, open a terminal and type in

```
sudo apt-get install flashplugin-nonfree
```

This is far simpler than navigating to Adobe's site (for which you haven't provided a link) then locating, downloading and installing the appropriate .deb package!  But remember, you must first remove any other flash packages you may have installed, such as the Free gnash plugin.

---

