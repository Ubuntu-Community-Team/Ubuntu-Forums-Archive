---
title: "Dell E6500 no WIFI"
date: 2010-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hammer2583 on 2010-03-03
I have heard rave reviews from many friends, stating that Ubuntu is the way, and it is the greatest os ever, i dont do any programming or anything, but i am no dummy when it comes to anything. Up until lately i thought i could do about anything, but it seems i stand corrected,  a dummy begging someone.......anyone to help me.

I have a dell latitude e6500, when i installed Ubuntu i lost my dash light for my wifi as well as my wireless adapter's functionality. When i use a usb adapter, it will work, and so does my switch for my internal wifi, but my internal adapter doesn't, and neither does the dash light for my wifi.

Please someone HELP

---

### Post by blkcamarozr28 on 2010-03-04
I just managed to get my Dell Latitude D400 wifi working after 3 days of mucking with Ubuntu 9.10. Here is the process that worked. 


sudo apt-get install b43-fwcutter
sudo apt-get install linux-backports-modules-karmic
sudo apt-get remove network-manager

reboot
Go into BIOS:
Look for Wireless setting and change it to "FN+X & Application" and wireless "ON"

Boot back into Ubuntu and reload network-manager.
sudo apt-get install network-manager
reboot

After the reboot network-manager showed the SSID's of other wifi networks in the neighborhood. Previously, it would show it all garbled and it would associate but never get a dhcp IP address. Hope this works for others. Also, you can try hitting the FN+F2 (whatever your soft key is to turn on your wifi).

---

### Post by gibbylinks on 2010-03-04
> **hammer2583 said:**
> I have heard rave reviews from many friends, stating that Ubuntu is the way, and it is the greatest os ever, i dont do any programming or anything, but i am no dummy when it comes to anything. Up until lately i thought i could do about anything, but it seems i stand corrected, _** a dummy begging someone**_.......anyone to help me.

I have a dell latitude e6500, when i installed Ubuntu i lost my dash light for my wifi as well as my wireless adapter's functionality. When i use a usb adapter, it will work, and so does my switch for my internal wifi, but my internal adapter doesn't, and neither does the dash light for my wifi.

Please someone HELP

Your no dummy. You are constantly learning until the day you die !!.  Never be afraid to ask questions, it's always better to look stupid than trash your OS or do something silly :P

Have you tried connecting by Cat 5 cable and installing the restricted drivers. Look for hardware drivers under system

---

### Post by spectralblue on 2010-03-04
> **gibbylinks said:**
> Your no dummy. You are constantly learning until the day you die !!.  Never be afraid to ask questions, it's always better to look stupid than trash your OS or do something silly :P

Have you tried connecting by Cat 5 cable and installing the restricted drivers. Look for hardware drivers under system


Ah, I remember the first time I tried installing ubuntu, and these proprietary drivers gave me headaches! I just wanted to use Ubuntu! lol

I would suggest, the easiest way of doing this is connecting your device via the Cat 5 cable as mentioned above (also known as an ethernet cable). Then what you would do is open up a terminal by pressing Alt+F2 and typing gnome-terminal

Type the following commands (entering your password whenever it prompts you).

```
sudo apt-get update
sudo apt-get upgrade

```To update your system first. 

Then, go to System>Administration>Hardware Drivers I believe and activate one of the drivers there if there's one. 

Otherwise, to activate proprietary drivers without internet, you'll have to download the packages yourself on another machine (or another OS), then you'll have to load it in the apt cache and install it from there, which might be complicated (not to mention annoying) for someone starting out with Ubuntu. 

Hope this helps!


EDIT: When you get your internet working, perhaps you might wanna download and read Keir Thomas' Ubuntu Pocket guide at : [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by RozNY on 2010-03-07
I got the WIFI working on my Dell Lattitude E6500 without having to muck with anything low level on Ubuntu 9.10

I first made sure that I had all the latest updates via System / Administration / Update Manager

I then sure that I had the wireless tools package and the latest network manger installed

sudo apt-get install wireless-tools
sudo apt-get install network-manager

I then went to System / Administration / Hardware Drivers
A Broadcom STA wireless driver (proprietary, tested by Ubuntu developers) was listed but shown as not activated. I activated it.

My wireless networking then worked.

---

