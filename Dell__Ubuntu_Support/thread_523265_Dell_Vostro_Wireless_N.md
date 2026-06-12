---
title: "Dell Vostro Wireless N"
date: 2007-08-11
forum: Dell  Ubuntu Support
---

### Post by driztin on 2007-08-11
I have a Dell vostro 1500 and I am new to linux in general . I have the internal Wirelss N card. I was able to get the correct driver for it from dell support. and I can install the driver in the GUI for ndsiWrapper. and it will connect and work. and I am able to use the wireless connection. UNTILL i reboot. I reboot the computer and the wireless device is no longer being detected. the driver is still showing installed with ndiswrapper but the only way i know how to get the device to work again is to uninstall and then reinstall the device driver.

---

### Post by Jamie Jackson on 2007-08-12
There are some things you need to do to make the settings "stick."

See "Step 3" of this [article]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") for ideas.

In particular, you might want these lines after adding the driver to ndiswrapper:
```

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules

```

---

