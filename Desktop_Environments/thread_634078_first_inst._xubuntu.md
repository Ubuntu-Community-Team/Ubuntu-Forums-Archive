---
title: "first inst. xubuntu"
date: 2007-12-07
forum: Desktop Environments
---

### Post by hirohitosan on 2007-12-07
Hello there. I just installed Xubuntu. I have I small problem installing java and flash. In fact I installed using "Applications>System>Add and remove", everything goes well but when I open Firefox the plug ins doesn't work.

Can you give me any suggestions?

Thanks

---

### Post by banewman on 2007-12-07
Firefox has its' own flash plugin.
From the bookmarks select customize firefox.
Then plugins and select adobe flash. :)

---

### Post by hirohitosan on 2007-12-07
well ... I downloaded flash pluin and 
```
sudo rpm -Uvh adobe-release-i386-1.0-1.noarch.rpm 

sudo: rpm: command not found

```
strange ... how can I install flash?

---

### Post by banewman on 2007-12-07
If you click the plugin from mozilla's site then it is installed for you.
rpm is a package manager not used in ubuntu - it is used by some other linux distros.

---

### Post by mali2297 on 2007-12-07
* Open the package manager Synaptic. 
* Go to the menu Settings->Repositories and enable the **multiverse** repository. 
* Use the Search function to find the packages **sun-java6-plugin** and **flashplugin-nonfree**. 
* To install a package, click the box next to it and choose Mark for installation. The dependencies will then also be marked.
* When you&#8217;ve finished, click Apply. View the Details screen during install, you might be asked to confirm a license agreement.
* Close Synaptic.

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by qiepenguin on 2008-03-03
> **daradib said:**
> This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

I would like to fix this on my 64-bit Gutsy installation (I have exactly the grey box problem discussed in the bug thread) but do not know how to build and install from the source.  Could someone help with instructions?

---

### Post by qiepenguin on 2008-03-03
> **qiepenguin said:**
> I would like to fix this on my 64-bit Gutsy installation (I have exactly the grey box problem discussed in the bug thread) but do not know how to build and install from the source.  Could someone help with instructions?

Oh, never mind, the compiled version is now available in 64-bit [_here_]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466")

---

