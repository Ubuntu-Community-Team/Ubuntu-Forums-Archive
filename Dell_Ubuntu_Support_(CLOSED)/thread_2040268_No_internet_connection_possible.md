---
title: "No internet connection possible"
date: 2012-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Xavier1 on 2012-08-10
Hi everyone,

I have a problem with my dell inspiron 1720, and I was hoping you could help me with it.

I had vista installed on the machine, with both wired and wireless internet working perfectly. I have recently installed 12.04 on it, and no internet connection seems to be possible at all.

After reading a bit on the web[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/"), I figured I hat to do a manual installation of the drivers for my network card (Broadcom 4311) from the boot media using Ubuntu Software Center. However, in order to install b43-fwcutter, I need an internet connection, which I unfortunately don't have.

Simply put, I really don't see how I could make my internet work at all... I would greatly appreciate your help in any way whatsoever. Thank you in advance!

---

### Post by unevenflow on 2012-08-10
hey go to: packages.ubuntu.com/ and search for and then download
**b43-fwcutter** and **firmware-b43-installer** packages
then in terminal type:
**sudo apt-get --purge remove bcmwl-kernel-source**
next right click in b43-fwcutter deb and choose open with ubuntu software center
do the same with firmware-b43-installer and finally from **Hardware/Additional Drivers** activate your driver and reboot.

---

### Post by Xavier1 on 2012-08-11
Thank you, I did just what you told me.

Unfortunately, the install button is still grayed out in Ubuntu Software Center when I try to install the b43-fwcutter package. It seems that an internet connection is needed in order to do an offline installation... Isn't that kind of a major flaw? I really can't see how to do it now.

---

### Post by wildmanne39 on 2012-08-11
Hi, 

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Thanks

---

### Post by Xavier1 on 2012-08-12
> **wildmanne39 said:**
> Hi, 

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Thanks

I get the following message after entering the sudo cp Desktop/b43/* /lib/firmware/b43 line:

no such file or directory

Then after the sudo rmmod -f ssb, I get:
Resource temporarily unavailable.

Thanks

---

### Post by wildmanne39 on 2012-08-12
Hi,  copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Xavier1 on 2012-08-12
> **wildmanne39 said:**
> Hi,  copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

I don't think this will be possible, as I don't have an internet connection at all...

---

### Post by wildmanne39 on 2012-08-13
Hi, did you download the file and extract it? Run the commands again one line at a time and copy and paste for accuracy.
Thanks

---

