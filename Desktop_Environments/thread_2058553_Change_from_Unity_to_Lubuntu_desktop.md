---
title: "Change from Unity to Lubuntu desktop"
date: 2012-09-16
forum: Desktop Environments
---

### Post by jbh000911 on 2012-09-16
I've installed Ubuntu 12.04 LTS and wish to get the Lubuntu desktop usable rather than Unity.
How do I go about this?

:)

---

### Post by Max Blyss on 2012-09-16
You should just have to install it...

Terminal - **sudo apt-get install lubuntu-desktop** should work.  Reboot, log in in an LXDE session, and configure to your liking.

---

### Post by Max Blyss on 2012-09-16
Oh, There's tutorials around for removing Unity after you do this if you wish.  Google's a beautiful thing, lol!

---

### Post by jbh000911 on 2012-09-16
Thanks max Blyss, it  worked fine.  I finally found the icons to the Lubuntu desktop behind the Ubuntu symbol on the login panel in Ubuntu 12.04. 

Question:  Does the distribution retain the LTS feature following the addition of the Lubuntu desktop and removal of the Unity desktop?

Thanks again, much appreciated.

:)

---

### Post by kansasnoob on 2012-09-17
> **jbh000911 said:**
> Thanks max Blyss, it  worked fine.  I finally found the icons to the Lubuntu desktop behind the Ubuntu symbol on the login panel in Ubuntu 12.04. 

Question:  **[COLOR="Red"]Does the distribution retain the LTS feature following the addition of the Lubuntu desktop and removal of the Unity desktop?[/COLOR]**

Thanks again, much appreciated.

:)

No!

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Lubuntu/Lubuntu-12.04#Support](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Lubuntu/Lubuntu-12.04#Support)

But using the "fallback mode" in Ubuntu w/o removing any packages is supported for the full five years:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

It ain't perfect but it's darn close :D

---

### Post by snowpine on 2012-09-17
Easy instructions to remove Unity, if you choose: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

The LTS question confuses a lot of people. Lubuntu 12.04 and Ubuntu 12.04 share the same repositories, which will be supported through April 2017. Your computer isn't going to explode or anything if you choose the LXDE desktop. :)

---

### Post by jbh000911 on 2012-09-17
Thanks for the info, much appreciated

---

### Post by claracc on 2012-09-19
> **kansasnoob said:**
> no!

[https://wiki.ubuntu.com/precisepangolin/releasenotes/lubuntu/lubuntu-12.04#support](https://wiki.ubuntu.com/precisepangolin/releasenotes/lubuntu/lubuntu-12.04#support)

but using the "fallback mode" in ubuntu w/o removing any packages is supported for the full five years:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

it ain't perfect but it's darn close :d

+1

---

### Post by offgridguy on 2013-01-19
Just found this thread,real handy as i want to try Lubuntu desktop. Thanks.

---

### Post by Frogs Hair on 2013-01-19
You can install the LXDE session without committing to Lubuntu desktop for trial purposes and use . ```
sudo apt-get install lxde
```

---

