---
title: "Dell Inspiron 1525 wireless"
date: 2008-03-30
forum: Dell  Ubuntu Support
---

### Post by wertyuiop408 on 2008-03-30
Thank you in advance for your help
i have the dell inspiron 1525, recently got a new hd for it and installed ubuntu. 
I need help getting the wireless working, it isnt shown in the network area (just shows wired and modem)
I have the 4310 card

solved thank to this link here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

---

### Post by johnnyleetsauce on 2008-05-23
I have the Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03). I'm using 8.04 32-bit. Following the instructions the first go around won't work. This is basically what I did.

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx


sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper


REBOOT


sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper; cd ~/bcm43xx/ndiswrapper
sudo wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz) -Ondiswrapper.tar.gz
tar xvzf ndiswrapper.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install


wget [http://myspamb8.googlepages.com/R151517-pruned.zip](http://myspamb8.googlepages.com/R151517-pruned.zip)
unzip R151517-pruned.zip

cd ~/bcm43xx
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo modprobe ndiswrapper
sudo ndiswrapper -m

Reboot and it should work :D

---

