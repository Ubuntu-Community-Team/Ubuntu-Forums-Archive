---
title: "Network problems on Dell 11z"
date: 2009-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by daahli on 2009-09-03
Hi,

I just bought a shiny new Dell 11z Inspiron for my girlfriend. The machine is quite nice, especially given the price. Of course the first thing I did was format the machine and install ubuntu (she wasn't too thrilled, but I promised to install winxp in a VM for her). 

Everything works except for the network (which of course is pretty critical). I can't get either the wired or wireless networks to work. The reported chipset is B4312 which is also known as the Dell 1397 wireless card. The driver appears as activated in the restricted drivers menu, but I can't see any networks, or even connect to the wired network.

Any ideas?

Thanks

---

### Post by Untergeher on 2009-09-05
Hey,

I have a very similar problem and I am still working on it. Do the following to find out about the Network Controller Chipset:

lspci | grep 'Network'

The output line you are looking for should include the name of the chipset, something like Broadcom Corp. BCM43xx ... This line should begin with some number. In my case it is 08:00.0. Run the command

lspci -n | grep '08:00.0'  (<- put your number instead).

The output includes the PCI ID. In my case, it is 14e4:4315 (rev 01). (Note that name and id do not have to coincide.)

However, with the name of the chipset and the pci id, you can look up the driver you need to download on 

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
and
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices).

They have instructions for you. It might be a little tricky to get it to work without alternate internet connection. 

Let me know if it worked,
untergeher

---

### Post by daahli on 2009-09-05
Thanks for the response. In the meantime I managed to get the wired network to work by doing the following:


1) Download the latest AR81Family linux driver at: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

2) Extract the downloaded file (I got some errors in the process but it still worked): 

tar -xzvf DOWNLOADED_DRIVER

3) Cd into the extracted src folder, compile and activate the driver:

make
sudo make install
sudo insmod atl1e.ko


Hope that helps if you're having wired issues.

In terms of the wireless, it looks like kernel 2.6.32 has support for this card (according to the link you posted). Looks like the latest Karmic Alpha 5 is at 2.6.31. Too bad, might have to wait until it get's updated.

---

### Post by mikewhatever on 2009-09-05
I have the same wireless card, B4312 on a Dell mini 10, and it worked out of the box.

> *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2c:1b:24:e5
       width: 64 bits
       clock: 33MHz


The wired is a Realtech, also worked out of the box

> description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:fa:e9:44
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz


Why don't you post the outputs of the following two commands:

sudo lshw -C network
ifconfig

---

### Post by daahli on 2009-09-05
Great news! The laptop works perfectly with Karmic Alpha 5. The wired network works out of the box. 

The wireless can be activated by going to system->administration->hardware drivers and then activating the B43 and STA drivers. Then reboot and viola!

Now I may be able to convince my girlfriend to stick with Ubuntu ;)

---

### Post by fjgaude on 2009-09-05
Be careful with 9.10 Alpha 5, lots of bugs yet to be removed!

---

### Post by Untergeher on 2009-09-05
Problem solved:

I told you I had the same problem. Dell 11z Broadcom 4312 (aka Dell 1397 half mini wireless). It appears to be a firmware problem. I fooled around the whole night to work around it. I didn't even have wired access, nothing worked. I tried out what I wrote you. Didn't work out, the system wouldn't load the new modules upon startup. I even looked for windows drivers, then I found drivers on [www.broadcom.com](www.broadcom.com) ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) which I considered trying out. But I had another idea first, a very pragmatic approach: I tried out Ubuntu 8.04 instead of 9.04.

Everything works out of the box with Ubuntu 8.04. I read about a bug in Jaunty, so I gave it a shot with 8.04.

Have a nice weekend,
untergeher

---

### Post by erlguta on 2009-11-19
I am thinking about buy this netbook. What about, sound, microphone, webcam..?. Does all it works ok?.
Thank you.

---

### Post by snebtor on 2009-12-20
Yes. It works great with 9.10!  I did the same as Daahli, only that I installed wicd instead of the gnome network manager and then I could see the wireless networks.  Also, in the preferences of wireless settings of wicd add 'eth0' in the wireless field.




> **daahli said:**
> Great news! The laptop works perfectly with Karmic Alpha 5. The wired network works out of the box. 

The wireless can be activated by going to system->administration->hardware drivers and then activating the B43 and STA drivers. Then reboot and viola!

Now I may be able to convince my girlfriend to stick with Ubuntu ;)

---

### Post by taxboy111 on 2010-01-06
Well... I´ve installed Karmic on Inspiron 11z; :popcorn: the wireless card didnt work out of the box, u just need to install all the updates and Voila!! :P i don´t know if the microphone works too, but BT does, and i´ve got a problem here, i´m trying to transfer Music, Documents and Images pc-cellphone and cellphone-pc and it says that an error occurred while transfering
 
Sorry but  my english isnt good :confused:

---

