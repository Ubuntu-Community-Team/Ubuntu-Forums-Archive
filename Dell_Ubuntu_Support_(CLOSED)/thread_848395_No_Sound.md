---
title: "No Sound"
date: 2008-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Stuart1941 on 2008-07-03
I have recentlty bought a new Laptop, it is a Medion 96640, 3gig memory intel core 2 duo 1.8ghz. I have installed Ubuntu 8.04 via the Wubi method, I have got the graphics working correctly but cannot get any sound, and also when i set up the wireless with my correct codes I have to do it every time I start Ubuntu how can I make it remember my network settings.
Stuart W

---

### Post by matttbe on 2008-07-26
I have MD 96640 too and now i haven't any problem with Ubuntu Hardy 64bit:

Sound : (from [http://doc.ubuntu-fr.org/audio_intel_hda](http://doc.ubuntu-fr.org/audio_intel_hda))

***************************************
sudo apt-get install build-essential
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
tar -jxf alsa-driver-1.0.16.tar.bz2
wget [http://poiresdujardin.free.fr/patch/patch_realtek_mitac8227.tar.gz](http://poiresdujardin.free.fr/patch/patch_realtek_mitac8227.tar.gz)
tar -xzf patch_realtek_mitac8227.tar.gz
rm alsa-driver-1.0.16/sound/pci/hda/patch_realtek.c
mv patch_realtek.c alsa-driver-1.0.16/sound/pci/hda/
cd alsa-driver-1.0.16/
./configure --with-cards=hda-intel --with-oss=yes
make
sudo rm /lib/modules/`uname
-r`/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
cp pci/hda/snd-hda-intel.ko /lib/modules/`uname
-r`/ubuntu/sound/alsa-driver/pci/hda/
sudo gedit /etc/modprobe.d/alsa-base
*** put in the end ***
options snd-hda-intel model=mitac
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
***************************************

(May-be if you have some problems with wifi Ralink :)
(from :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/216084/comments/10](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/216084/comments/10))
download the last firmware and driver for RT2860 from
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
copy the firmare to /lib/firmware (sudo cp rt2860.bin /lib/firmware/`uname
-r`)
extract driver to ~/driver
******************
cd ~/driver
gedit os/linux/config.mk ######### change : HAS_WPA_SUPPLICANT=n =>
HAS_WPA_SUPPLICANT=y    and   HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n =>
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
sudo -s
make
make install
modprobe rt2860sta
ifconfig ra0 up
gedit /etc/network/interfaces ######### put on the end 'auto ra0'
/etc/init.d/networking restart

     ////// * Reconfiguring network interfaces...
Ignoring unknown interface ra0=ra0.
     //////
[ OK ]

ps faux | grep NetworkManager

     ////// root      5634  0.0  0.0  52532  2268 ?        Ssl  22:02
0:00 /usr/sbin/NetworkManager --pid-file
/var/run/NetworkManager/NetworkManager.pid
     ////// root      5648  0.0  0.0  28384  1420 ?        Ss   22:02
0:00 /usr/sbin/NetworkManagerDispatcher --pid-file
/var/run/NetworkManager/NetworkManagerDispatcher.pid
     ////// root      9019  0.0  0.0   5172   840 pts/0    S+   22:27
0:00          \_ grep NetworkManager

kill 5634
kill 5648
/usr/sbin/NetworkManager --pid-file
/var/run/NetworkManager/NetworkManager.pid
/usr/sbin/NetworkManager --pid-file
/var/run/NetworkManager/NetworkManagerDispatcher.pid
**********************
after that, install wicd (it's better than NetworkManager for Ralink
firmware I think)
(add 'deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras' to sudo gedit
/etc/apt/sources.list)
(sudo apt-get update)
(sudo apt-get install wicd)

---

