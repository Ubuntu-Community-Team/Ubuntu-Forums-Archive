---
title: "AMD Beta drivers 12.11  :  Additional Drivers"
date: 2012-11-23
forum: Gaming &amp; Leisure
---

### Post by Magbed on 2012-11-23
Hi there i would like to know when are the new Ati beta 12.11  drivers going to be available on the additional driver menu in ubuntu 12.04.

I know you can get them by enabling proposed ppa... but i dont like  updating all my packages to still on testing packages...

---

### Post by QIII on 2012-11-23
If you stick with the 12.04 repo, I believe you'll see only the 12.4 driver.  I think that was ATI's 8.960 development branch.

---

### Post by mentorious on 2012-11-23
I don't believe that the drivers will be available in Ubuntu 12.04. That's beta!

I have also ATI graphics cards (ATI Mobility HD5650) and FireGL drivers in the application "Additional Drivers" in Ubuntu 12.10. I installed Catalyst 12.11.8 only for steam, but they work veeery good, much better than stable fglrx version.

Here you can find tutorial "how to install" these drivers: [http://www.gry.ubuntu-pomoc.org/publiczna-beta-steam-jeszcze-przed-swietami/](http://www.gry.ubuntu-pomoc.org/publiczna-beta-steam-jeszcze-przed-swietami/)

Yeap, it's not in english but the commands are simple. Firstly you need to delete the old driver:

```
sudo apt-get remove --purge fglrx*
```download binary from [official site ]("http://support.amd.com/de/gpudownload/Pages/index.aspx")for your current card (important - your card must be supported, choose correct model in searchbox)

run install file:
```
sudo chmod +x amd-driver-installer-catalyst-12.11-beta-x86.x86_64.run
``````
sudo sh amd-driver-installer-catalyst-12.11-beta-x86.x86_64.run
```

After install generate new xorg:
```
sudo aticonfig --initial
```

and reboot your pc :)

---

### Post by Magbed on 2012-11-24
Hi thnx all for the help, i think i will go the manual way for installing them.

Would like to know if everytime theres a new updated kernel will i have to reinstall the ati drivers manually? or should i ignore those kernel updates? or if it will work out of the box with new kernels?

Thanks again

---

### Post by Dlambert on 2012-11-24
You will need to reinstall the driver every time the kernel is updated.

---

### Post by QIII on 2012-11-24
If you use the package in the repo, you will not have to reinstall when the kernel is updated.  That will be taken care of by the update process.

---

