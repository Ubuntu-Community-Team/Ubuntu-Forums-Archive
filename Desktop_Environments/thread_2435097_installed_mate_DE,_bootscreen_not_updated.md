---
title: "installed mate DE, bootscreen not updated"
date: 2020-01-16
forum: Desktop Environments
---

### Post by bluepicaso2 on 2020-01-16
Hi,
few days ago I installed mate desktop environment to reduce some memory consumption. I might have installed mate DE may be a year ago then removed it.
If I remember correctly, after uninstalling mate DE, my boot screen was still showing  mate boot screen. so I did.
```

sudo update-alternatives --remove default.plymouth /usr/share/plymouth/themes/ubuntu-mate-logo/ubuntu-mate-logo.plymouth
sudo update-alternatives --remove default.plymouth /usr/share/plymouth/themes/ubuntu-mate-logo/ubuntu-mate-logo-scale-2.plymouth
sudo update-alternatives --remove text.plymouth /usr/share/plymouth/themes/ubuntu-mate-text/ubuntu-mate-text.plymouth         

```
Now I have installed mate DE again but boot screen is still showing up ubuntu boot screen.
Command: ```
sudo update-alternatives --config default.plymouth
```
gives error:
```
There is only one alternative in link group default.plymouth (providing /usr/share/plymouth/themes/default.plymouth): /usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.
```

I am using Ubuntu 18.04

Please help

---

### Post by bluepicaso2 on 2020-01-16
SOLUTION
```
 sudo apt install --reinstall plymouth-theme-ubuntu-mate-logo
```

```
 sudo apt install --reinstall plymouth-theme-ubuntu-mate-text
```

---

