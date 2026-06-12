---
title: "Installing Flash plugin error"
date: 2006-09-22
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-09-22
Hi all,

Keep getting this on install:

Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas on how to correct this?

Thank you.

---

### Post by p.i.m.p on 2006-09-22
i had the same error, so i downloaded the flash plugin off their website.. 

sudo dpkg -r flashplugin-nonfree 

download
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

extract the archive and run the flashplayer-installer script

when it asks for the path to the browser enter /usr/lib/firefox

---

### Post by Ramses de Norre on 2006-09-22
[This](http://www.ubuntuforums.org/showpost.php?p=1525778&postcount=62) worked for me.

---

### Post by The Pinny Parlour on 2006-09-22
Thanks guys.  Will give them a try. :)

---

