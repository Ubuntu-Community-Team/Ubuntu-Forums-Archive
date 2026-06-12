---
title: "When will Open Office 3 be in Synaptic?"
date: 2009-02-01
forum: General Help
---

### Post by frankwakeman on 2009-02-01
I downloaded a tar.gz of Open Office 3, but it seems quite a hassle to install it and I don't want to mess up Ubuntu or get further away from the simple installation methods I was used to with Windows.

Should the suite be in Synaptic soon?  What holds this sort of thing up?  Apparently even this April's version of Ubuntu will still have 2.4. though Mandriva and Suse have 3.

If anyone gives any advice could they please made it jargon-free and assumption-free.

Thanks.

---

### Post by adamlau on 2009-02-01
OO3 has been available for a couple of months now. Add the following to your sources list:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

Or if you are on Intrepid Ibex: 

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

Reload, search for openoffice and install from there.

---

### Post by Crafty Kisses on 2009-02-01
It's not that hard at all, follow this guide: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml).

---

### Post by mb_webguy on 2009-02-01
It will be in Synaptic as soon as you a) upgrade to Jaunty Jackalope, or b) add the [openoffice-pkgs PPA]("https://launchpad.net/~openoffice-pkgs/+archive") to your software sources.

Since Jaunty won't be officially released for a few more months, I'd suggest the latter.

To add the PPA's key, click on the long, ugly alphanumeric link.  On the subsequent page, right-click on the keyID link and save the link to your computer.  Then, on the Authentication tab of Software Sources, click the Add button and locate the file you just downloaded.

---

### Post by Cheesehead on 2009-02-01
Open Office 3.0.1 is currently in the Jaunty (9.04) repositories. So it will show up in Synaptic in April if you take no other action.

---

### Post by ubuntu27 on 2009-02-01
I don't when OpenOffice is going to be imported for Ubuntu 8.10, i think it was suppose to be when OpenOffice.org 3.0.**1** has been released..
But, version 3.1 is already out and we have not received any udates yet.

Maybe it was version 3.1?

[http://www.tectonic.co.za/?p=3447](http://www.tectonic.co.za/?p=3447)



Anyway, for those of us who are not patient, we can add [PPA for OpenOffice.org Scribblers]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") repository


[Here is a guid]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")e that explains how to install OpenOffice.org 3 step by step with graphics.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by abn91c on 2009-02-01
[/QUOTE][Here is a guid]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")e that explains how to install OpenOffice.org 3 step by step with graphics.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)[/QUOTE]
+1 this is the best guide, the same steps works great with kubuntu 8.10 also

---

### Post by snowpine on 2009-02-02
Just to be clear, OO3 will *never* automatically appear in Synaptic if you're running Intrepid. The reason for this is that Ubuntu never uprades an application automatically to a new major release, only minor upgrades such as bug fixes. You need to add the repository mentioned above (or install the files directly from the OO website) if you want OO3.

---

### Post by philinux on 2009-02-02
> **snowpine said:**
> Just to be clear, OO3 will *never* automatically appear in Synaptic if you're running Intrepid. The reason for this is that Ubuntu never uprades an application automatically to a new major release, only minor upgrades such as bug fixes. You need to add the repository mentioned above (or install the files directly from the OO website) if you want OO3.

If it were to appear in Intrepid it would come from the backports team. You have to enable that repo in software sources>updates.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by frankwakeman on 2009-02-02
I'd like to mark this and some of my other posts as solved, but how I'd go about this seems to be a secret as far as I can tell.

Thanks all.

---

### Post by jerome1232 on 2009-02-02
Just because I don't like adding repo's from some blog and adding a key that that blogger says is the real public gpg key.

Here's the actual ppa for open office

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by Hooya on 2009-02-02
> **frankwakeman said:**
> I'd like to mark this and some of my other posts as solved, but how I'd go about this seems to be a secret as far as I can tell.

Thanks all.

The [Solved] function is currently not available.  So don't worry about it.

---

