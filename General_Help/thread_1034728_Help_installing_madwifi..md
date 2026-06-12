---
title: "Help installing madwifi."
date: 2009-01-09
forum: General Help
---

### Post by Buttons840 on 2009-01-09
Me and a friend have spent hours trying to get Ubuntu 8.10 installed and working on his Aspire One.  Were both really new to Linux.  We've been fallowing the guide below:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

It's installed and working, but we can't get the wireless to work.

First, we tried 2 different drivers in ndiswrapper, because I was semi-familiar with it.  They didn't work.  We did:

```
sudo ndiswrapper -i driver.inf
ndiswrapper -l        (driver is listed)
sudo depmod -a
sudo modprobe ndiswrapper
```

After we tried to 2 drivers, we uninstalled them from ndiswrapper.

```
sudo ndiswrapper -r driver
```

Now were trying madwifi, which apparently should work better, according to guide.
```

wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
modprobe ath_pci
```

The computer we are trying to install on has no internet connection.  I downloaded the file [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz), and unzipped it.  Navigated to that directory and did:

```
sudo make
sudo make install
sudo modprobe ath_pci
```

It's not working.

What does sudo apt-get install build-essential linux-headers-$(uname -r) do?  I'm not sure what this command means?  Other than that I think I understand the others.  (Although I don't understand modprobe and all that stuff.)

Any tips or help would be appreciated.  Thank you.

---

### Post by Buttons840 on 2009-01-09
I fixed it.  Nevermind.

---

### Post by nothingspecial on 2009-01-09
build-essential is software that allows you to compile stuff from source.

modprobe is the command to load a module(driver)

ath_pci is the (module) driver you just got from madwifi

---

