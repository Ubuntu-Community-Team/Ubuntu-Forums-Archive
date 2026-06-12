---
title: "Replace Ubuntu Gnome3 14.04 with Ubuntu Unity 14.10"
date: 2014-10-29
forum: Desktop Environments
---

### Post by anirudhkodaru15 on 2014-10-29
How to do I replace the Ubuntu GNOME 14.04 LTS with GNOME Desktop Environment with an Ubuntu 14.10 Unity Desktop Environment?

---

### Post by Rob Sayer on 2014-10-29
The first thing I'm wondering is why do you want 14.10 instead of 14.04?  14.04 is an LTS release and supported for 5 years for unity or gnome DEs.  For the others you're looking at updating or reinstalling every 6 to 9 months.  If there was any configuring you had to do, you cannot assume the same method will work on the next release.

I've had non LTS releases on my netbook before 14.04 because I had Linux hardware support issues with it.  Fortunately they've been solved AFAIK in 14.04.  There is no other reason I'd use a non LTS release.  It's highly unlikely there are any new features that are that dazzling.

But if you really want to change ... or just change the DE from gnome to unity ... I'd actually do a clean reinstall.  It's more reliable than upgrading.  You do need data backups though.

if you do so, especially if you really want 14.10, try setting it up with a separate partition for /home.  Then when you upgrade again in 6-9 months you don't lose data or user settings (you still want your data backed up though).  Search here or askubuntu for details.

Reinstalling would definitely be better IMO if you want to change DEs.  Otherwise you're probably looking at doing an upgrade then installing the unity desktop.  Having 2 DEs is not all that reliable a setup and purging one of 2 GTK based DEs can be tricky.

---

### Post by ajgreeny on 2014-10-29
> **Rob Sayer said:**
> The first thing I'm wondering is why do you want 14.10 instead of 14.04?  14.04 is an LTS release and supported for 5 years for unity or gnome DEs.  For the others you're looking at updating or reinstalling every 6 to 9 months.  If there was any configuring you had to do, you cannot assume the same method will work on the next release.

I've had non LTS releases on my netbook before 14.04 because I had Linux hardware support issues with it.  Fortunately they've been solved AFAIK in 14.04.  There is no other reason I'd use a non LTS release.  It's highly unlikely there are any new features that are that dazzling.

But if you really want to change ... or just change the DE from gnome to unity ... I'd actually do a clean reinstall.  It's more reliable than upgrading.  You do need data backups though.

if you do so, especially if you really want 14.10, try setting it up with a separate partition for /home.  Then when you upgrade again in 6-9 months you don't lose data or user settings (you still want your data backed up though).  Search here or askubuntu for details.

Reinstalling would definitely be better IMO if you want to change DEs.  Otherwise you're probably looking at doing an upgrade then installing the unity desktop.  Having 2 DEs is not all that reliable a setup and purging one of 2 GTK based DEs can be tricky.
+1
I couldn't agree more; I can see little point in now using an intermediate version of Ubuntu, unless as Rob Sayer says, you have hardware problems with the current LTS version.

14.04.1 is rock-solid now with no stability issues, which you can bet your boots, will not be the 14.10 situation for a month or two, and a month or two out of the nine months support for 14.10 is a huge chunk.

---

### Post by grahammechanical on 2014-10-29
Another answer would be, you cannot. We can install an alternative desktop but only of the same version. So, if you installed Ubuntu Desktop on to Ubuntu Gnome 14.04 it would be the 14.04 Ubuntu Desktop because that is the version in the repositories.

Ubuntu and its flavours share the same repositories. And each version has separate repositories. The repositories for 14.04 are labelled "trusty" and the repositories for 14.10 are labelled "utopic." They are two different locations on the Canonical servers.

I agree with what has been said above. Installing alternative desktops is not something we do and then change our mind later. It is easy to install an alternative desktop it is not so easy to remove all evidence of its existence. Except by re-installing.

Both Ubuntu 14.04 and 14.10 use the Unity 7 user interface. No difference there. And now that Ubuntu and the flavours have reached the 14.04.1 version the Linux hardware stack should be the same as that on 14.10.

So, if it is your desire, then install Ubuntu desktop onto Ubuntu Gnome. But do not try to remove the Gnome 3 shell = Trouble.

Regards.

---

### Post by anirudhkodaru15 on 2014-10-29
Yes I do love the present status of my system. Working perfectly!
But anyways thanks a lot! That was some valuable information!

Okay so I have one question in mind. . Let's say I want to keep my version as it is i.e. I want to keep it as Ubuntu 14.04 LTS Release.

**How do I change my DE from Gnome to Unity?**

Are there any specific steps or precautions that I supposed to know about. Because this my first time fiddling with a DE! :)

Thanks a lot once again!

---

### Post by anirudhkodaru15 on 2014-10-29
Thanks a LOT! :D

---

### Post by anirudhkodaru15 on 2014-10-29
Thank you thank you! :)

---

