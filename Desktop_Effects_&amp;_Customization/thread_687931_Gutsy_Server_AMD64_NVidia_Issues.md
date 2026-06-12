---
title: "Gutsy Server AMD64 NVidia Issues"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by wiseguyxp on 2008-02-04
I am running an Ubuntu 7.10 server with the NVidia drivers installed from the site.  Every time I want to enable custom desktop effects, it wants me to install the restricted driver.  I tried installing the restricted driver, but it doesn't work and boots into failsafe X.  Is there a way to either keep the driver I have and make custom desktop effects work, or maybe a way to make the restricted driver work?

---

### Post by pdub on 2008-02-04
Make sure you have disabled the nvidia restricted modules.

```
sudo nano /etc/default/linux-restricted-modules-common
```

DISABLED_MODULES="nvidia nvidia_legacy" 


Then delete the following file if it exists.

```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```


You may have to reinstall the binary nvidia driver again from the nvidia site.

---

### Post by wiseguyxp on 2008-02-04
I deleted the file and in DISABLED_MODULES, I had "nvidia_new and Nvidia_legacy" disabled to begin with, but I disabled the ones you said to also, and the same issue occurred.  The restricted driver installed, X came up failsafe at next boot.  I reinstalled the driver from the site and i'm in the same place I was before.

---

### Post by pdub on 2008-02-04
What happens if you do the following

```
ctrl + alt + F1
```

login 

```
sudo /etc/init.d/gdm stop

sudo rmmod nvidia

sudo modprobe nvidia

sudo /etc/init.d/gdm start
```

---

### Post by wiseguyxp on 2008-02-04
strange, I tried it again and it worked.  thanks for your help!

---

