---
title: "Compiz Desktop Cube won't work"
date: 2009-11-14
forum: Desktop Environments
---

### Post by robinzxp on 2009-11-14
My problem is that compiz Desktop Cube won't work. After enabling the option, I press ctrl + alt + down and it does nothing. I changed work space to 2 by 2 also. Any ideas?

I'm using Ubuntu 9.10 and have ATI x800 graphics card. I'm not sure if I need to install proprietary ATI driver to work?

---

### Post by John Bean on 2009-11-14
Workspaces should be 4x1 to use the cube sensibly.

---

### Post by robinzxp on 2009-11-14
Ok, it does some kind of line thing now but it still not 3d cube and ctrl alt click isn't work either.

---

### Post by robinzxp on 2009-11-14
Bump

---

### Post by realzippy on 2009-11-14
Run:

**glxinfo | grep direct**

You need direct rendering for Compiz.Check *System/Administration/Restricted-drivers* for offered ATI drivers.

---

### Post by John Bean on 2009-11-14
> **robinzxp said:**
> Ok, it does some kind of line thing now but it still not 3d cube and ctrl alt click isn't work either.
ctrl-alt plus left or right arrows should rotate it, and a mouse centre-click-drag will do anything you want. There are other keys/mouse actions but those will test that it's working.

---

### Post by Tickborn on 2009-11-14
> **robinzxp said:**
> My problem is that compiz Desktop Cube won't work. After enabling the option, I press ctrl + alt + down and it does nothing. I changed work space to 2 by 2 also. Any ideas?

I'm using Ubuntu 9.10 and have ATI x800 graphics card. I'm not sure if I need to install proprietary ATI driver to work?

Hi,
Many functon of Compiz worked for me only after installing updated driver for the Ati 4800 serie. I would give it a try:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by bandad on 2009-11-14
My newly built AMD64 with GeForce 9800GT with two monitors also doesn't do the cube thing.

Compiz Settings manager shows all the right boxes ticked, but nothing.

I am using the nvidia X server settings utility, and have set the system to use twinview...

```
Section "Screen"
# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: nvidia-auto-select +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Is twinview the problem?

---

### Post by realzippy on 2009-11-14
> **bandad said:**
> My newly built AMD64 with GeForce 9800GT with two monitors also doesn't do the cube thing.

Compiz Settings manager shows all the right boxes ticked, but nothing.

I am using the nvidia X server settings utility, and have set the system to use twinview...

```
Section "Screen"
# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: nvidia-auto-select +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Is twinview the problem?
[I]
That is threadnapping.But set it to "0" to find out![/I]

---

### Post by bandad on 2009-11-14
I found the answer for my question.
Twinview is NOT the problem. I now have it working.

Solution (for me): unselected the "Detect Outputs" option on the "Display Settings" tab under "General Options" on CompizConfig Settings Manager.

I also had to play with the outputs a bit to get the effects I wanted.
(see [this post]("http://ubuntuforums.org/showpost.php?p=2913064&postcount=5"))

---

### Post by robinzxp on 2009-11-14
Hey, realzippy thanks for reply on my other topic also.

Sounds like by looking at what Tickborn say I need to install ATI proprietary driver for 3d effects to work. Some of stuffs like expo, ring switcher already works.

I checked *System/Administration/Restricted-drivers* but there is nothing in the list. I tried "sudo apt-get install fglrx" but I get
*"E: Couldn't find package fglrx"*

I tried also following
*[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)*
but I get

[I]kyung@kyung-desktop:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
Package `linux-restricted-modules-2.6.31-14-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-restricted-modules-2.6.31-14-generic is not installed.[/I]

Any ideas on how to install ATI proprietary driver?

ps. I just want to add that in my Software source I have propretary drivers for devices box ticked.

---

### Post by Tickborn on 2009-11-14
> **robinzxp said:**
> Hey, realzippy thanks for reply on my other topic also.


Any ideas on how to install ATI proprietary driver?

ps. I just want to add that in my Software source I have propretary drivers for devices box ticked.

Did you try the link i gave you before?

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Here you can select your Linux drive. On thepage you also find instructions. It is pretty easy anyway, the download includes aninstall program to be started in the konsole.
It worked out fine for me.

---

### Post by realzippy on 2009-11-14
> **Tickborn said:**
> Did you try the link i gave you before?

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Here you can select your Linux drive. On thepage you also find instructions. It is pretty easy anyway, the download includes aninstall program to be started in the konsole.
It worked out fine for me.

And using Karmic**?**

---

### Post by robinzxp on 2009-11-14
Yep, I am on 9.10.

I tried following ATI site instruction and get this error after it uncompresses.

[I]Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro[/I]

---

### Post by realzippy on 2009-11-14
May somebody correct me,but the X800 needs the 9.3 ATI driver which needs old Xorg version....so:
To get best 3D acceleration for this card you should "downgrade" to 8.10 Intrepid Ibex where needed Xorg is used.BTW 8.10 is rocksolid meanwhile...no loss of features.

*edit:"And using karmic?" was adressed to Tickborn...*

---

### Post by Tickborn on 2009-11-14
> **realzippy said:**
> And using Karmic?

Yes i am. I installed the driver  for 4800 series, version x86_64. had no problems, or at least i don't recall i got any error message; and especially now it works! :)

---

### Post by realzippy on 2009-11-14
> **Tickborn said:**
> Yes i am. I installed the driver  for 4800 series, version x86_64. had no problems, or at least i don't recall i got any error message; and especially now it works! :)

is it the same driver?

---

### Post by realzippy on 2009-11-14
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) :

JAUNTY NOTICE

    *

      The above Jaunty 9.04 instructions don't actually work because the latest ATI driver is incompatible with XOrg 1.6. To see a guide on instructing how to downgrade XOrg and install the ATI driver, view this link:
    *

      [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by Tickborn on 2009-11-14
> **realzippy said:**
> is it the same driver?
That i don't know, Robin should answer. What i installed is  an "ati-driver-installer-9-10-x86.x86_64.run" for a 4850 board. The included installation file worked fine, following the instructions from AMD; after installation, graphic improved, and Applications menu inludes an ATI Catalyst Control Center that seems also to do its job.
I am not sure if it could work even better: up to know i did not observe any problem. Any idea how could i test it?
In the link you included, they talk about *older* ATI; is the 4850 already to be included in the older group? (ehy, answer "no": i bought it only few months ago ;) )

---

### Post by robinzxp on 2009-11-15
Hey I'm not sure what you're asking but I tried "ati-driver_installer-9-3-x86.x86_64.run" but it didn't install.

---

### Post by realzippy on 2009-11-16
Again:

"don't actually work because the latest ATI driver is incompatible with XOrg 1.6"

Install Inrepid Ibex to use the ATI-driver !!

---

