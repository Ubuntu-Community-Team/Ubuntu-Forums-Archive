---
title: "Vdrift Installtion Query"
date: 2006-07-27
forum: Gaming &amp; Leisure
---

### Post by _simon_ on 2006-07-27
Haven't tried this for a fair while so thought I'd try the latest.

I downloaded "vdrift-2006-07-08-full.x86.package" from the vdrift website and started the install.

I've not seen an install like this and want to make sure it's legit before I type in my password as it's requesting I do....

```

The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of http://autopackage.org/downloads/latest/autopackage.tar.b z2 ...
--11:54:56--  http://autopackage.org/downloads/latest/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://autopackage.org/downloads/latest/logger.php [following]
--11:54:56--  http://autopackage.org/downloads/latest/logger.php
           => `autopackage.tar.bz2'
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ftp.sunsite.dk/projects/autopackage/1.0.10/autopackage.tar.bz2 [following]
--11:54:56--  http://ftp.sunsite.dk/projects/autopackage/1.0.10/autopackage.tar. bz2
           => `autopackage.tar.bz2'
Resolving ftp.sunsite.dk... 130.225.247.92
Connecting to ftp.sunsite.dk|130.225.247.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 864,355 (844K) [application/x-tar]

100%[====================================>] 864,355      227.94K/s    ETA 00:00

11:55:01 (217.03 KB/s) - `autopackage.tar.bz2' saved [864355/864355]

Download completed.

```

I then get a non standard pop-up box come up asking me to enter my password. For now i've just cancelled the install until someone can reasure me this is normal and safe!

---

### Post by xen on 2006-07-27
Yep this is normal, however I couldn't get past this point for other annoying reasons!

---

### Post by Perfect Storm on 2006-07-27
That's normal. Though if you don't trust the source, don't install it.

---

### Post by thelusiv on 2006-08-14
You don't have to install as root. That's one of the nice things about autopackage. Just don't enter your password and it will install it in your home directory under /home/you/.local/ .

If you can't get past the part where it asks for a password, you don't have all the necessary stuff installed. Install libopenalut and try again. I made the package and couldn't figure out how to make it report to the user when that package was missing...

---

