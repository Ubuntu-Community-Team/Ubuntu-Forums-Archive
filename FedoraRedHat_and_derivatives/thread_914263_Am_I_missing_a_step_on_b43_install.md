---
title: "Am I missing a step on b43 install"
date: 2008-09-08
forum: Fedora/RedHat and derivatives
---

### Post by BSG75 on 2008-09-08
I am trying to install the firmware for my broadcom chip in fedora 9. I used this command.
```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

It installs correctly, until I enter the sudo password then it tells me that my username is not in the sudoers file. The driver file is in the fwcutter file, but my chip still will not work

---

### Post by Antman on 2008-09-08
> **BSG75 said:**
> I am trying to install the firmware for my broadcom chip in fedora 9. I used this command.
```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

It installs correctly, until I enter the sudo password then it tells me that my username is not in the sudoers file. The driver file is in the fwcutter file, but my chip still will not work
The Sudo command is not working because, as the error message stated, your user name isn't listed in the /etc/sudoers file. Ubuntu has sudo activated by default, but Fedora (and must other linux distros) doesn't. Try becoming root first with:
```
su
```
than try using your commands above.

---

