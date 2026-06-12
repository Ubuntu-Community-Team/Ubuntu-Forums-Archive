---
title: "Install OpenOffice 3.0 in 8.10?"
date: 2008-12-15
forum: Desktop Environments
---

### Post by RX8volution on 2008-12-15
Hi everyone.  I'm new to this so sorry if this is a silly question.  The 8.10 version comes with OO.org 2.x, how do I "upgrade" it to 3.x?

Thanks!

---

### Post by gettinoriginal on 2008-12-15
Right here:  :p

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by motostar on 2008-12-15
Check this out
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

this worked for me. hope this helps you aswel :)

---

### Post by Vantrax on 2008-12-15
Remove the old version:
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer

Download:
wget [http://openofficeorg.secsup.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz](http://openofficeorg.secsup.org/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz)

Extract:
tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

Install:
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/
sudo dpkg -i *.deb

Then install the desktop integration package:
cd desktop-integration
sudo dpkg -i *.deb

All done

---

### Post by Joe2Shoe on 2008-12-18
I updated OO.org to v3.0 using Synaptic Package Manager.
Works fine.

---

### Post by markharding557 on 2008-12-18
just for any one reading add this to your sources list
> deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

---

### Post by manilaph on 2009-02-09
Hi,

I've gone through a number of threads with the same topic of "installing OpenOffice 3" but there are some differences.

Just to clarify, as I understood the posts, this is what should be done (please correct if I am wrong):

1) Remove all traces of OpenOffice via 
Remove the old version:
**sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer**


2) Once the old version is removed, ADD the following to sources:
[B]deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main[/B]

3) Refresh/Reload Synaptic to recognize the newer OpenOffice, then use Synaptic to install OpenOffice 3.

My question, in Synaptic... will it show what version of OpenOffice is available?


Could I simply un-install OpenOffice using Step #1 and then go to the OpenOffice website and do the downloading of "Linux.deb" over there?

I read on another version of this topic that if you download straight from the openoffice.org website, it will not be fully-customized for Ubuntu... is this correct?

---

### Post by calc on 2009-03-04
> **manilaph said:**
> Hi,

I've gone through a number of threads with the same topic of "installing OpenOffice 3" but there are some differences.

Just to clarify, as I understood the posts, this is what should be done (please correct if I am wrong):

1) Remove all traces of OpenOffice via 
Remove the old version:
**sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer**


2) Once the old version is removed, ADD the following to sources:
[B]deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main[/B]

3) Refresh/Reload Synaptic to recognize the newer OpenOffice, then use Synaptic to install OpenOffice 3.

My question, in Synaptic... will it show what version of OpenOffice is available?


Could I simply un-install OpenOffice using Step #1 and then go to the OpenOffice website and do the downloading of "Linux.deb" over there?

I read on another version of this topic that if you download straight from the openoffice.org website, it will not be fully-customized for Ubuntu... is this correct?

I'm pretty sure step one is only needed if you are trying to install the official openoffice.org debs from their website. It shouldn't be needed for the ppa debs. If they don't upgrade that would be a bug and should be filed in launchpad against the openoffice.org (ubuntu), the best way to do this is via openoffice.org program help -> report a problem.

The official openoffice.org website debs will not cleanly upgrade from Ubuntu and when you upgrade to a new version of Ubuntu it also will not cleanly upgrade until you remove those debs. This means you have to remove all the Ubuntu openoffice.org packages before installing the official debs and then before you upgrade Ubuntu you need to remove the official debs first. The official debs also do not include any of the integration and extra bug fixes that are in the Ubuntu version. The Ubuntu version has many extra bugfixes and features since it uses Go-OO (ooo-build).

---

### Post by knightstar76 on 2009-03-09
> **gettinoriginal said:**
> Right here:  :p

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

OK.... I just followed these instructions it took 2min to do 10min to dload and 5min for the updates to run... Worked great... I give you five stars for this one...
:KS:KS:KS:KS:KS

---

### Post by c2tarun on 2010-11-09
> **markharding557 said:**
> just for any one reading add this to your sources list



what if i m using lucid do i just write lucid on the place of intrepid??

---

