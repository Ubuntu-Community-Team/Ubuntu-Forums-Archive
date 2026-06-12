---
title: "Scanner broken with recent update"
date: 2006-07-03
forum: Desktop Environments
---

### Post by jonboy99 on 2006-07-03
Has anyone else had this?  Have scanjet3300c which until recently has been working fine.
However today both xsane and openoffice do not appear to recognise it, although oddly openoffice will get a preview image from it but won't aquire an image I can import.

I booted into another partition with dapper drake on it which I haven't updated for a while, and both xsane and openoffice work fine.

I presume the fact openoffice has also stopped working rules out a problem with xsane itself, as this is just a graphical front end for the scanner engine, although have tried uninstalled and reinstalling.  Not tried installing a non repo version 0.99 yet as am not convinced this is the problem and don't want to break dependencies.


Any ideas?

---

### Post by barisurum on 2006-07-03
Did you try to reinstall "sane" and "libsane"?
   I had the same problem with my hp 6110 when I upgraded to dapper. The xsane looked for devices and said "no devices found". So I reinstalled xsane, sane, libsane. After that I also editted the "etc/sane.d/dll.conf" and commented all devices that I don't need support for. I restarted the printer/scanner and it worked.

---

