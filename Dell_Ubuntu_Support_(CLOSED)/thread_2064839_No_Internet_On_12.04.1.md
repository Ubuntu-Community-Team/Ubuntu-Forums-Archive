---
title: "No Internet On 12.04.1"
date: 2012-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Drado on 2012-09-30
**[COLOR="Red"]I have no internet on Ubuntu 12.04.1 so i'm on a desktop so I got to install a .exe program to run my wireless card for my desktop so I got internet access, But I can't seem to download wine or its source files. If I do I put on my usb and boot into Ubuntu but then when I try to open it I get the programs source files etc. Anyone who could help me Please do  ( I can't install wine from software center since I have no connection online).[/COLOR]**

**[COLOR="Black"]Note : I can download my stuff on windows 8 boot so I can transfer files to my usb to run on Ubuntu.[/COLOR]**

---

### Post by andriansah on 2012-09-30
this is what i do with my laptop inspiron 5420
To activate wire network

Install compat wireless with this version

compat-wireless-2012-02-28-p

./scripts/driver-select alx

make

sudo make install

reboot and plug in your wire network

 

After you wired network up now its time fire up the wireless

download this file

It’s here: [http://wielki.tk/vostro/debs/wlan_amd64.deb](http://wielki.tk/vostro/debs/wlan_amd64.deb)

sudo dpkg -i wlan_amd64.deb

first time it will fail then you have to do

sudo apt-get -f install

then it will get all file need to install wlan_amd64.deb

reboot your laptop

 

all done

---

### Post by Sonsum on 2012-09-30
If you let us know what wireless card you are using, we may be able to get you more specific instructions.

[Here's]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") a page with all the supported video cards.

---

### Post by Drado on 2012-10-01
I am using N600 Wireless Dual Band USB Adapter
WNDA3100

---

### Post by Drado on 2012-10-01
> **Sonsum said:**
> If you let us know what wireless card you are using, we may be able to get you more specific instructions.

[Here's]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") a page with all the supported video cards.

I am using a N600 Wireless Dual Band USB Adapter
WNDA3100

---

### Post by Joseph Rinaldi on 2012-10-24
Hi,
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, [FONT=Calibri]ndiswrapper-dkms and ndiswrapper-source.[/FONT]
[FONT=Calibri]2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box).[/FONT]
[FONT=Calibri]3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.[/FONT]
[FONT=Calibri]4. Copy the folder to your Ubuntu (or Xubuntu) computer.[/FONT]
[FONT=Calibri]5. Run the Windows Wireless Drivers software and point to the inf file in this folder.[/FONT]
[FONT=Calibri]6. Reboot. All done![/FONT]

---

