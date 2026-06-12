---
title: "Open Office 3"
date: 2008-10-23
forum: Desktop Environments
---

### Post by GaryLittlemore on 2008-10-23
Does anyone know when Open Office 3 will be coming to Ubuntu via the 'Update Manager'?

Any help would be great.

---

### Post by ThaRabbit on 2008-10-23
> **GaryLittlemore said:**
> Does anyone know when Open Office 3 will be coming to Ubuntu via the 'Update Manager'?

Any help would be great.

Ubuntu releases get security updates only, perhaps some major functionality additions here and there in terms of kernel updates.

It is therefore unlikely that open office 3.x will be available through the ubuntu repositories for 8.04 and below.

You can, however, grab the .debs from the openoffice site and install that. They can co-exist perfectly. If you like openoffice 3.x you can manually remove 2.4x

---

### Post by kpkeerthi on 2008-10-23
If you are lucky someone may backport it [here]("https://help.ubuntu.com/community/UbuntuBackports")

---

### Post by conscious on 2008-10-23
"OpenOffice 3.0.1, to be released on Dec. 2, is a bugfix only release and should prove to be much more stable than the current release. This release will be available on the backport repository."

Developer response, [http://brainstorm.ubuntu.com/idea/14433/](http://brainstorm.ubuntu.com/idea/14433/)

---

### Post by Teniser on 2008-10-23
Where i can download Open Office 3.0 for Ubuntu 8.04 (Linux i686)? I search for .deb installation! Thanks.

---

### Post by swisscow on 2008-10-23
For download try the openoffice website. Note for 64bit, it ain't there so do a google search for the 64bit deb

---

### Post by Teniser on 2008-10-23
The site does not .deb installation. Whether someone has a link to the .deb installation?

---

### Post by swisscow on 2008-10-23
Yes it does. Here's the link

[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

### Post by Teniser on 2008-10-23
Sorry! Thanks a lot to link.

---

### Post by swisscow on 2008-10-23
My pleasure. Good luck with it. There are lots of debs so to install easily extract the tar file by right clicking, choose extract here.

Cd into the folder (assuming it's on your desktop), open a terminal and then

cd Desktop
cd OOffice......(name of foldere here)
sudo dpkg --install --recursive ./DEBS (enter your password)
cd DEBS
cd desktop-integration
sudo dpkg --install *.deb


NB, I found it better to remove openoffice 2.4 first - I did a search in synaptic and removed everything to do with openoffice

---

### Post by jdong on 2008-10-23
*Backports Team Leader hat ON*

I talked to our Openoffice guru extensively about the state of OOo3, and from what I gathered he's not very confident that the "final" release is all that polished. We also realized that the packaging we had from Hoary (yikes!) for installing two versions of Openoffice beside each other was pretty messed up and probably not fixable without substantial effort or a rewrite.

Given these two:

(1) Since Intrepid is supposed to be a more 'daring' release, at 3.0.1 we will offer backports to replace the shipped copy of Openoffice with 3.0.1
(2) Since Hardy is a LTS and expected to be more stable, I'd like to wait at least a month AFTER (1) to assess if we want to replace the default Openoffice with this release.


I will also note that Ubuntu has been using an ooo-build release of OpenOffice (unlike the official releases) which incorporate a lot of the cool enhancements in version 3 (such as office 2007 compatibility) already, which should make the wait a bit less painful.



I appreciate everyone's patience and understanding on this as we proceed with this update in a carefully planned, well thought out manner.

---

