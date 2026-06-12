---
title: "Herd4 issues on 32 and 64bit"
date: 2007-02-17
forum: Development CD/DVD Image Testing
---

### Post by davmor2 on 2007-02-17
I have just done a fresh install on my 64bit and 32bit and have noticed the following:

1.  The partitioner has no format in rename feature.  (ie you have to click on format after you have named a partition '/' or '/home')  This is a waste of time as it resets the settings twice. #85909
2.  Neither install rebooted they both just logged out after the install. (when the message saying restart now or continue live session) #85853
3.  Neither version ejected the cd after I had selected rebooting from login prompt. #58503
4.  In sources normally Multiverse and Universe are unticked both were ticked (I don't know if this is to make it easier for installing media codecs or just an error) #85908
5.  The firefox window opened with an extra tab saying it was just updated. Probably go away by next release.
6.  Hardware Database is not in applications/system tools again (this problem got remedied and now is back) #83324
7.  Still two network icons on the taskbar. #83330

Bug numbers to follow.....

---

### Post by jerrylamos on 2007-02-17
Hardware information - 

When the hardware database entry was moved to Applications, System the "hardware information" selection was removed from Control Center altogether and should not have been, see bug #85421.

Hardware information is restored to the control center on 20070217.  At the bottom of the data it does have the entry to optionally return hardware info to the developers.

I didn't see the request on initially booting up for hardware info.

Since I run on more than one computer (5) the hardware information selection in the control center is usefull, especially when having crashes like I am having today.

Cheers, Jerrry Amos:)

---

### Post by davmor2 on 2007-02-18
But the message that pop up still says it is located in apps/sys tools where is quite obviously isn't :)

---

### Post by kuja on 2007-02-20
Not a bug:

Quote from [https://wiki.kubuntu.org/FeistyFawn/Herd4/Kubuntu](https://wiki.kubuntu.org/FeistyFawn/Herd4/Kubuntu)

> "Adept Changes
Adept has had another overhaul here, bringing new features, bug fixes, and probably the biggest and most wanted change, Universe and Multiverse repositories being enabled by default."

---

