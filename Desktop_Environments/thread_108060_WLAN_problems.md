---
title: "WLAN problems"
date: 2005-12-24
forum: Desktop Environments
---

### Post by Lmanovic on 2005-12-24
Hi,

A while ago my pc was connected directly to my modem, I installed ubuntu and internet worked fine....

I moved this pc into another room and I'm using linksys WLAN to connect. In windows it works.. but in Ubuntu it doesnt...

What do I do?
Thanks

---

### Post by Gooks on 2005-12-24
I also have the same problem as you . I want to have wireless on my laptop. I am currently running on wired internet. I am using an Linksys WRT45G.

---

### Post by reckless2k2 on 2005-12-24
As in Windows, you will need the driver in order to get your wifi to work in Linux. Take a look here and it should be able to answer all your questions:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

Good luck.

---

### Post by Lmanovic on 2005-12-25
That's like Chinese to me.. I don't really know what to do ...

---

### Post by Gooks on 2005-12-25
Yeah its to me t&#7885; But i finish everything i just need to get my driver. I dont know what is my driver. Can somebody get my driver for m&#7867;

---

### Post by towsonu2003 on 2005-12-25
it's surprisingly a poor wiki... see this for a complete list of drivers & where to get them [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

to find your wlan in there, issue a ```
lspci
``` and find your wlan in there. mine looks like this: ```
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

note this part```
0000:02:02.0
``` and do ```
lspci -n
``` and find the matching string in there (you are looking for the pciid), mine is this ```
0000:02:02.0 0280: 14e4:4320 (rev 03)
``` thus my pciid (for wlan card) is 14e4:4320. 

now go to that link and search for your pciid. There will possibly be a number of advices. choose one and start trying ;) good luck...

---

### Post by reckless2k2 on 2005-12-25
Gooks and Lmanovic,

If you guys are still having trouble getting this to work, please post back with the following:

Gooks - what is the make and model of your laptop? is the wireless card internal or external? if it is external, what is the make and model? if the card is internal, run this from the terminal as suggested by  towsonu2003:

lspci

report the findings under ethernet controller. Here is an example of mine:

0000:02:01.0 Ethernet controller: Intel Corp. 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Lmanovic - What is the make and model of the PCI or USB wifi card you have attached to your PC? If it is internal, follow the same instructions laid out for Gooks using lspci in a terminal window. 

I can then post back the steps and driver needed.

---

### Post by Lmanovic on 2005-12-25
I really don't have a clue what to do with it..
I have the same wireless card as you
My pciid = 0000:02:02.0 0280: 14e4:4320 (rev 03)

---

### Post by reckless2k2 on 2005-12-26
Based on what you've said, you the following wifi PCI card on your PC:

Card: Belkin 54g Wireless Desktop Network Card (F5D7000) Rev 03

    * Chipset: BCM4306
    * pciid: 14e4:4320
    * Driver: [http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE) (use bcmwl5a.inf in directory AR)

That info was retrieved from the ndiwrapper driver list here: 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

The following link will give you the driver you need:

[http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)

You need to extract it more than likely in Windows then burn to a CD more than likely to save it over to Ubuntu. If you have the driver CD from Belkin, you could just copy that which would be easier. The driver info specifically says to use the bcmwl5a.inf in the AR folder. So once you get it over to Ubuntu, you need to do the following:

nstall ndiswrapper-utils: System->Administration->Synaptic Package Manager. Search for ndiswrapper. Click on the box to install ndiswrapper-utils. Click Apply to install it. (If there are errors, perhaps try Reload to refresh package lists). Close it.

Now you'll install that driver in Ubuntu. Open a terminal window as such Applications -> Accessories -> Terminal (Going on that you saved the AR folder to your home directory):

$ sudo ndiswrapper -i /home/whateveryourloginnameis/AR/bcmwl5a.inf
$ sudo modprobe ndiswrapper
$ sudo ndiswrapper -m

Now use the terminal to open the interface file as such:

$ sudo nano /etc/network/interfaces

The edit like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

# The primary network interface
iface wlan0 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless_mode managed
wireless_essid REPLACE WITH YOUR ESSID
# dns-* options are implemented by the resolvconf package, if installed
#dns-nameservers 192.168.2.1

auto wlan0

Save that file and reboot your PC. You will then have wireless working. That was spelled out pretty plain. 

Good luck.

---

### Post by Lmanovic on 2005-12-26
thanks alot reckless but i dont understand the last part 

> 
The edit like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

# The primary network interface
iface wlan0 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless_mode managed
wireless_essid REPLACE WITH YOUR ESSID
# dns-* options are implemented by the resolvconf package, if installed
#dns-nameservers 192.168.2.1

auto wlan0

Save that file and reboot your PC. You will then have wireless working. That was spelled out pretty plain.

How do i enter that and what is my essid

thanks

---

### Post by reckless2k2 on 2005-12-26
I have no idea what wireless router you have. I don't know the manufacturer of your wireless router that would be connected to your cable/dsl modem. They all have a configuration page which would be the "address" of your router (ie. 192.168.0.1). All this information would be contained in the instructions for your wireless router. 

ESSID = SSID 

For example, Linksys usually uses the name linksys as it's SSID. D-Link uses default and Belkin typically uses something like Belkin54g as thier default SSIDs.

If you do not have a wireless router, you can not be connecting to the internet wirelessly.

---

### Post by Lmanovic on 2005-12-26
ok the address is 10.0.0.138 and linksys is the ssid.. but what i dont understand is what i do with all that typing.. do I enter it in the console? and where do I save it?

Thanks

---

### Post by reckless2k2 on 2005-12-27
From the terminal, you want to type the following:

$ sudo nano /etc/network/interfaces

nano is a text editor.

/etc/network is the location in Ubuntu

interfaces is the file that you are going to edit with nano.

Right now when you open the fiel it should look like this:

-------------------------------------------------------------------

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface
iface eth0 inet dhcp

-------------------------------------------------------------------


You want to edit the file to look like this:

--------------------------------------------------------------------

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
#map eth0
map wlan0

# The primary network interface
# iface eth0 inet dhcp

# The wireless network interface
iface wlan0 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless_mode managed
wireless_essid linksys

auto wlan0

--------------------------------------------------------------------

That should be fine. By putting # in front of 

map eth0
and
iface eth0 inet dhcp

It basically disables it. I suggest that if you will be primarily using the wifi card. 

Make sure to follow the other ndiswrapper setup instructions prior.

---

### Post by cborge on 2006-01-17
Hi.

I have installed ndiswrapper 1.7 and downloaded my wlan driver

I have done this:
$ sudo ndiswrapper -i /home/whateveryourloginnameis/AR/bcmwl5a.inf

But when I try the next step:
$ sudo modprobe ndiswrapper
I get an error. It says:


> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/misc/ndiswrapper.ko) Invalid argument  



Anyone? Please!

---

### Post by reckless2k2 on 2006-01-19
ndiswrapper is already installed on ubuntu as stated in this previous thread. if you are compiling from the source withe a more recent version of ndiswrapper, you'll need the source, headers, etc.. Follow the complete notes via the link posted in the first page about compiling from source. You'll just need to add the packages using synaptic which is referenced. Too bad you took the hard road but it's not terribly hard and you'll learn a little on the way.

---

