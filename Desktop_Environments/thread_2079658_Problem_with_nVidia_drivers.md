---
title: "Problem with nVidia drivers"
date: 2012-11-02
forum: Desktop Environments
---

### Post by samalex on 2012-11-02
Hi everone,

While trying to fix a problem I ran 'dpkg --configure -a' which reconfigured everything and hosed my NVidia drivers.  I finally got the video going again at normal resolution, but when I go into the NVIDIA X Server Settings then X Server Display Configuration I get this:

```
Unable to load X Server Display Configuration page:

The NVIDIA X driver on neptune:0.0 is not new
enough to support the nvidia-settings Display Configuration 
```

Here are the nvidia drivers I have installed:

```
rc  nvidia-173       173.14.35-0ubuntu0.2 
ii  nvidia-common     1:0.2.44.2                               
ii  nvidia-current    295.40-0ubuntu1.1 
ii  nvidia-current-updates       304.43-0ubuntu0.1
ii  nvidia-settings              295.33-0ubuntu1
ii  nvidia-settings-updates     304.43-0ubuntu0.2
```

And here's my video controller:

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [GeForce G 105M] (rev a1)
```

And if this matters in the Additional Drivers section i do have the NVIDIA accelerated graphics driver (version-current) one activated.  Oh, and I'm running XUbuntu 12.04 with all current updates.  Any suggestions?  It was working like a boss before, but now I'm not sure what to try next.

Thanks for any suggestions.

---

### Post by samalex on 2012-11-02
I got it working, though just by chance I think.

I downloaded the [304.60 drivers]("http://www.nvidia.com/object/linux-display-amd64-304.60-driver.html") from NVIDIA's website and booted into Text to install them, which installed fine, then X never would start.  So I uninstalled all the nvidia packages, which I didn't realize would also remove xdesktop, then I reinstalled xdesktop along with the nvidia-current and nvidia-current-updates packages, and after another reboot it's working and I'm now able to change my settings in the nvidia X configuration app.

So not sure exactly what I did other than probably just reset everything, but it's working so I'm not complaining :)

---

