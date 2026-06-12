---
title: "acroread 8 availability"
date: 2009-04-18
forum: General Help
---

### Post by r.stiltskin on 2009-04-18
(Ubuntu 8.04)

Is it still possible to install acroread 8 with Synaptic or apt-get?  I only find acroread 9.1.0-7 listed.

I tried apt-get install acroreac=8.1.3-0medibuntu... bla bla bla but either I wasn't using the correct string (I tried several) or it's just not there anymore.

Is it only available as acroread_8.1.3.orig.tar.gz (at [http://packages.medibuntu.org/hardy/acroread.html)?](http://packages.medibuntu.org/hardy/acroread.html)?)

---

### Post by rmockler on 2009-04-18
I'm using:  AdobeReader_enu-8.1.3-1.i386.deb

---

### Post by drs305 on 2009-04-18
It looks like you can get the 8.1.4 deb from here:

[http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")

**Added:** It looks like 8.1.3 is still in the Medibuntu repositories, at least the 64-bit is listed for hardy, intrepid and jaunty. Do you have medibuntu added to your repository list?

Perhaps you have "proposed"/"backports" enabled in your repositories, as I don't show 9 being available in the normal repos.

---

### Post by r.stiltskin on 2009-04-19
Yes I have 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
in my repo list, but I can't seem to get anything but 9.1.0-7hardy1 with Synaptic or apt-get.
apt-cache show acroread only lists Version 9.1.0

The only deb package I see on the medibuntu site is for amd64.

Thanks, I'll save a copy of that 8.1.4 deb from Adobe's html site, and I also found the 8.1.3 version at their ftp site:
[ftp://ftp.adobe.com/pub/adobe/reader/unix/8.x/8.1.3/enu/](ftp://ftp.adobe.com/pub/adobe/reader/unix/8.x/8.1.3/enu/)

Anything special that I need to know about regarding using them in conjunction with the acroread-plugins package (8.1.3) that is still listed on Synaptic?

It seems strange that acroread-plugins is listed by apt-get and Synaptic, yet on this medibuntu page:
[http://packages.medibuntu.org/hardy/acroread-plugins.html](http://packages.medibuntu.org/hardy/acroread-plugins.html)
the only deb package listed is for amd64.  Where does medibuntu list the packages that are available through Synaptic and apt-get?

---

### Post by drs305 on 2009-04-19
> **r.stiltskin said:**
> Where does medibuntu list the packages that are available through Synaptic and apt-get?

You can take a look at the several medibuntu entries /var/lib/apt/lists (free, non-free, etc). They have names starting with "packages.medibuntu". These files detail the available packages. 

To see just the package names, you could type "cat /var/lib/apt/lists/FILENAME | grep "Package" to just see the names.
For instance, on my 64-bit machine, with the medibuntu repo enabled:
```
cat /var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages | grep Package
```
For non-64-bit, you would have to substitute something where the "amd64" is listed, perhaps "i386". You would have to check the filenames.

---

### Post by r.stiltskin on 2009-04-19
Thanks, that confirms that acroread is no longer there (for i386).

---

### Post by r.stiltskin on 2009-04-27
Following up on this, I find that on one of my machines (a desktop), acroread-8.1.3-0medibuntu0.8.04.1 is listed in the output of ```
sudo apt-cache show acroread
```  It is also listed by Synaptic **if** I de-select the [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner repository.  (And it is, in fact, the version I have installed on that machine.)

But on my laptop *using the exact same sources.list* this package is not listed by "apt-cache show acroread" and does not appear in Synaptic's listing.

How is this possible?  Is it that the package is no longer available from medibuntu but it is cached somewhere on the desktop?  If so, can I copy it to another machine?  Or is it listed as the latest package available merely because it is installed, even though it is no longer available, so that if I uninstalled it I would not be able to reinstall it?

---

### Post by frogotronic on 2009-05-20
> **r.stiltskin said:**
> Following up on this, I find that on one of my machines (a desktop), acroread-8.1.3-0medibuntu0.8.04.1 is listed in the output of ```
sudo apt-cache show acroread
```  It is also listed by Synaptic **if** I de-select the [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner repository.  (And it is, in fact, the version I have installed on that machine.)

But on my laptop *using the exact same sources.list* this package is not listed by "apt-cache show acroread" and does not appear in Synaptic's listing.

How is this possible?  Is it that the package is no longer available from medibuntu but it is cached somewhere on the desktop?  If so, can I copy it to another machine?  Or is it listed as the latest package available merely because it is installed, even though it is no longer available, so that if I uninstalled it I would not be able to reinstall it?

yep you got it - they got pulled - don't whatever you do upgrade to 9.0 - it SUCKS

---

