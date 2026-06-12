---
title: "Emerald Themes -- Not taking effect unless I reload emerald"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by bjtuna on 2007-11-01
I have two machines, both running Gutsy. On one, if I go to Emerald Theme Manager and click on a new theme, it takes effect.  But on the other, it does nothing... the theme won't take effect unless I manually run 'emerald --replace'.  What's different? How do I get themes to switch on-the-fly?

Thanks!

---

### Post by bjtuna on 2007-11-01
Okay I think I know what's going on.  I did a little digging, and it seems like for themes to take effect immediately, Emerald has to be running against AIGLX, not Xgl.  My affected machine is running Xgl because it has an ATI video card, and at the time of Gutsy's release, the binary drivers from ATI (fglrx) did not support AIGLX.  This would also explain why I have a 350mb Xgl process on my system, eating my system resources like hogs at the trough. 

The good news, though, is that the new ATI drivers were released on 10/26/07 and have AIGLX support.  I'm going to wait for the Ubuntu guys to get it into the respositories, even though I saw a thread in which some folks got it running on Gusty already.

Hope this helps someone else.

---

### Post by Zorael on 2007-11-01
I believe the latest version of Envy will install that driver for you, although you'd be straying from the official repositories. If it isn't the 8.42.3 driver you're referring to, don't mind me.

> 2) the new ATI driver 8.42.3 is available, however I have to say a few things about it:

    * Compiz might be a bit slow, at least on my X1600 (make sure you’re using Compiz 0.6 or higher)
    * Driver 8.42.3 doesn’t support ATI Workstation cards (FireGL) therefore, if you own a FireGL card, Envy will install version 8.40.4
    * As AMD admits in the release notes, version 8.42.3 doesn’t work with Debian/Ubuntu 64bit, however Envy uses a patch which fixes this problem (Thanks to Aric Cyr and Mario Limonciello)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Forlong on 2007-11-02
> **bjtuna said:**
> The good news, though, is that the new ATI drivers were released on 10/26/07 and have AIGLX support.  I'm going to wait for the Ubuntu guys to get it into the respositories
That's defenitely the best way to go. The latest fglrx driver is too buggy right now with Compiz/AIGLX.

---

### Post by mk4umha on 2007-11-02
> **bjtuna said:**
> Okay I think I know what's going on.  I did a little digging, and it seems like for themes to take effect immediately, Emerald has to be running against AIGLX, not Xgl.  My affected machine is running Xgl because it has an ATI video card, and at the time of Gutsy's release, the binary drivers from ATI (fglrx) did not support AIGLX.  This would also explain why I have a 350mb Xgl process on my system, eating my system resources like hogs at the trough. 

The good news, though, is that the new ATI drivers were released on 10/26/07 and have AIGLX support.  I'm going to wait for the Ubuntu guys to get it into the respositories, even though I saw a thread in which some folks got it running on Gusty already.

Hope this helps someone else.


THanks for the info, i have 2 machines and the one running X with the 82852/855GM Integrated Graphics Device updates Emerald immediately. My other computer with a Geforce 7400 Go had problems with memory leaks with just X so i changed over to XGL and it won't update without reloading.

---

