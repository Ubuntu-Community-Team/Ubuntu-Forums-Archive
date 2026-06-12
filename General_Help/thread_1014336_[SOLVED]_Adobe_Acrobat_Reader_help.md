---
title: "[SOLVED] Adobe Acrobat Reader help"
date: 2008-12-17
forum: General Help
---

### Post by Camilia on 2008-12-17
I have a membership form that I need to fill out. It requires Adobe Acrobat Reader to fill it out. I have downloaded xpdf-common, Xpdf-reader, lesstif2
Lib1-5, Xpdf-utils and still not able to fill the form out. I can only read it. Tried saving it to documents.  

What other program do I need to type on the form?

---

### Post by Vantrax on 2008-12-17
Install medibuntu repository
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Update medibuntu GPG Key
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Install
sudo aptitude install acroread acroread-plugins mozilla-acroread

That will install the adobe reader program for you (assuming you are using hardy, change it to intrepid for intrepid)

---

### Post by OrangeCrate on 2008-12-17
> **Camilia said:**
> I have a membership form that I need to fill out. It requires Adobe Acrobat Reader to fill it out. I have downloaded xpdf-common, Xpdf-reader, lesstif2
Lib1-5, Xpdf-utils and still not able to fill the form out. I can only read it. Tried saving it to documents.  

What other program do I need to type on the form?

[B]Edit:

On first read, I missed the acroread plugins install info in the above post. I'll go ahead and leave this for others, but it's duplicate info.[/B]

-----

Once you have the Mozilla plugin installed, you'll need to be sure that the "acroread plugins" package is installed too. You can find that package in Synaptic.

From the package description...

> Plugins for Adobe Acrobat(R) Reader

Adobe Reader is an Adobe Portable Document Format (PDF) files viewer.

This package contains plugins that notably:
(1) enable completion of fillable forms,
(2) enable javascript in acroread and thus make acroread able to
send to a remote host which pdf files you are reading. See
[http://lwn.net/Articles/129729/]](http://lwn.net/Articles/129729/])


---

### Post by AllanPoe on 2008-12-17
Or, alternatively, go to [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/) , choose to download a.deb package and install it.

---

### Post by Camilia on 2008-12-17
Vantrax I followed your instructions and now it works.

Unreal how quick I got help at this forum.

---

### Post by slickvguy on 2009-02-19
Just a quick note to save some from potential frustration...

I tried to install Acrobat Reader as per the instructions above (as well as instructions found on various websites via google) but encountered a snag.

I needed the plugin installed because I use pdf forms and you can't edit forms without the plugin. However, the current version of Reader that automatically downloaded and installed ended in 0.8.10.2 while the plugin was 8.04.1 and required Reader to be the same (previous) version. Thus the installer attempted to downgrade the installed Reader to the previous version that plugin and mozilla acroread required - but the downgrade failed (not sure why). 

So I removed everything that had been previously installed to start "fresh" and then downloaded (saved) the .deb package from Adobe's website and opened with the deb package manager. That worked!

---

### Post by Camilia on 2009-02-19
Uploaded ubuntu again from CD, for accidently errased programs which enabled boot up. This time went to 
[http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")
Downloaded linux deb and clicked open

---

