---
title: "Network setup"
date: 2007-09-25
forum: Colorado Team - US
---

### Post by mwredt on 2007-09-25
I have always used Windows but want to convert to Ubuntu.  I got the cd's for version 7.04 and installed just fine but cannot get my network going.  I want to connect to a network that I already have installed.  I am using a D-link DI-524 router.  My ISP provider is Alltel and I am using their Speedstream 5200 ADSL modem.
I used another computer to get online and download instructions from ubuntu website under Internet.  In the computer where I installed Ubuntu I have a D-Link DWL-520 vE1 wireless card.  This is one that is not supported so I am trying to set up ndiswrapper like the instructiions say.  To see if ndiswrapper is working, in Terminal  I type ndiswrapper -1.  I get the message "The program 'ndiswrapper' is currently not installed.  You can install it by typing:  sudo apt-get install ndiswrapper-common".
I do this then the following comes up:

Reading package lists...Done
Building dependency tree
Reading state information...Done
E:  Couldn't find package ndiswrapper-common

I did have my Ubuntu CD in the drive.  What else do I have to do?

I have been trying for some time to get Ubuntu installed and working with my network. Before v7.04 I was trying with version 5.??.  Everything is new to me and it is difficult to understand what I am to do.  It seems that nothing works as it is supposed to.
Can anyone help me?  I really want to get Ubuntu installed and working so I can put it on all my computers (I have four).

---

### Post by Whelpo on 2007-09-26
My suggestion would be to temporarily hardwire the Ubuntu machine to your router via ethernet cable and then once you have an active internet connection run the following command within a command prompt:

sudo apt-get install ndisgtk
(you should be prompted for a password at this point)

This should download and install a graphical front end for ndiswrapper-common as well as download and install ndiswrapper-common itself.

Once that is installed, unplug the ethernet cable and use and ndisgtk to setup your wifi card. You will also need to have the windows drivers for that wifi card available (download them from the manufacturers website while you are still hardwired if you have to) since ndiswrapper is supposed to make the windows drivers usable in linux from my understanding.

---

### Post by Jon.d.snow on 2007-09-27
The key to that is you need to connect to a network with internet access in order to grab and install the ndiswrapper package. Also keep in mind ndisgtk sometimes doesn't report the driver loaded correctly (BCM53WL5 drivers with ndisgtk does this often) . 

As long as you connect hardwired and follow the instructions you had located (Something along these lines: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)) ) You should be running wireless within a few minutes.

---

### Post by arook1427 on 2008-07-29
Attempt network installation via professionals. 
Cnce you've gathered your [network cables]("http://www.cxtec.com/products/cables/"), routers, modems, etc...Call Cxtec for further installation assistance or visit our informational site at cxtec.com.  We're adding a knowledge base full of information about wireless security.:)

---

