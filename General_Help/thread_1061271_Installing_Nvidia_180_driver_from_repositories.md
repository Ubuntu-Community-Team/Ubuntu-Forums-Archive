---
title: "Installing Nvidia 180 driver from repositories"
date: 2009-02-05
forum: General Help
---

### Post by douham on 2009-02-05
I note that the Nvidia 180.11 driver is currently in the Intrepid repo. How do I install the repo driver rather than download from nvidia and go through the Ctrl F1, sudo stop GDM, sh Nvixxxx process?

Doug

---

### Post by hyper_ch on 2009-02-06
I thought a 179.xx is in the repos... but I could be mistaken there. Use the Restricted Driver Manager to install the repo version of the nvidia driver.

---

### Post by ju2wheels on 2009-02-06
```

sudo apt-get install nvidia-glx-180 nvidia-180-modaliases

```

Didnt realize that was packaged already, it never suggested I upgrade mine in the Hardware Driver panel (guess Ill file that for a feature request later).

---

### Post by douham on 2009-02-07
> **ju2wheels said:**
> ```

sudo apt-get install nvidia-glx-180 nvidia-180-modaliases

```

Didnt realize that was packaged already, it never suggested I upgrade mine in the Hardware Driver panel (guess Ill file that for a feature request later).

Thanks ju2wheels. I was looking at some of the community help on compiling and it looked a lot more complicated than that.

---

### Post by u235sentinel on 2009-03-25
> **douham said:**
> Thanks ju2wheels. I was looking at some of the community help on compiling and it looked a lot more complicated than that.

I'm curious if these 180 drivers would work with Ubuntu 8.04.  I'm running the 169 driver and was curious if there was any further updates after that.

Been looking around and found the Intrepid drivers but am a bit cautious before installing and breaking what already works.  

The hope is to improve my gaming with TF2/CSS under WINE.  

Thus my motivation and question :D

thanks!

---

### Post by ju2wheels on 2009-03-25
The non intrepid branded packages here [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/) should work out fine.

Check out my previous post here: [http://ubuntuforums.org/showpost.php?p=6695171&postcount=5](http://ubuntuforums.org/showpost.php?p=6695171&postcount=5)

---

### Post by u235sentinel on 2009-03-25
> **ju2wheels said:**
> The non intrepid branded packages here [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/) should work out fine.

Check out my previous post here: [http://ubuntuforums.org/showpost.php?p=6695171&postcount=5](http://ubuntuforums.org/showpost.php?p=6695171&postcount=5)

Awesome!  I'll check it out tonight.  Thanks!

---

