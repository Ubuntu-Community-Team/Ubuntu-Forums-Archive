---
title: "Wireless Network USB Adapter Drivers"
date: 2009-06-24
forum: General Help
---

### Post by SamJosRob on 2009-06-24
Hello. I'm a fairly new user to Linux, as I only installed Ubuntu 8.04 a few days ago. My desktop doesn't have a wireless card, so I stupidly bought a wireless USB adapter. The drivers for the adapter are on a disc, and it is only compatible with windows. So, I install Wine and am at least able to run the .exe . When the drivers begin to install, it fails. I'd rather get this to work somehow instead of taking it back to the store. 

For the record, [here]("http://www.linksysbycisco.com/US/en/products/WUSB100") is the wireless network adapter.

Thank you in advance, and I'm sorry if I'm not up to speed at this point. Since I'm new, I appreciate the help and patience.

---

### Post by keplerspeed on 2009-06-24
You will need ndiswrapper.

Firstly, do you have an internet connection, and what version is your wireless stick? 1.0 or 2.0? [http://www.linksysbycisco.com/US/en/support/WUSB100/download](http://www.linksysbycisco.com/US/en/support/WUSB100/download)

Once we know that I can help with ndiswrapper.

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> You will need ndiswrapper.

Firstly, do you have an internet connection, and what version is your wireless stick? 1.0 or 2.0? [http://www.linksysbycisco.com/US/en/support/WUSB100/download](http://www.linksysbycisco.com/US/en/support/WUSB100/download)

Once we know that I can help with ndiswrapper.

It's version 2. I've actually downloaded that already, but wasn't very successful in using it

---

### Post by nice_like_rice on 2009-06-24
As keplerspeed said, you need ndiswrapper to use the xp drivers (make sure you use the XP ones not the vista ones).

The driver should be on the CD, and is called rt2870.inf.

---

### Post by keplerspeed on 2009-06-24
Well, we will be sucessfull with ndiswrapper! What did you download? we Will need:

ndisgtk
ndiswrapper-common
ndiswrapper-utils-1.9

---

### Post by keplerspeed on 2009-06-24
SamJosRob, we need to know if you have an internet connection, and if it is on this machine running 8.04.

If you do, go to system>admin>synaptic and search for ndiswrapper and install those.

If not, either download from another machine or use the install cd, they are on the install cd.

---

### Post by keplerspeed on 2009-06-24
Once you have those installed, we need the .inf file. I have it here: [http://www.keplerspeed.comuv.com/rt2870.inf](http://www.keplerspeed.comuv.com/rt2870.inf)

Download that (right click, save link as), and then go to system>admin>windows wireless drivers, and navigate to the .inf file. and thats it!

---

### Post by SamJosRob on 2009-06-24
I have ndiswrapper and a wired connection to the internet, and I also did as Nice like rice said and got the rt2870.inf. driver. Ndiswrapper detects it, and with the usb network adapter plugged in it detects the hardware.

---

### Post by keplerspeed on 2009-06-24
And you have a wireless connection?

---

### Post by SamJosRob on 2009-06-24
I'm afraid not. This may be my general lack of know how, but when I unplug my Ethernet cord, no wireless networks are detected. Am I going about this wrong, or should a wireless network be detected automatically?

---

### Post by keplerspeed on 2009-06-24
Plug in the usb wireless adapter and have the ethernet unplugged.

Right click on the network icon in the top right of screen, is the 'enable wireless' box ticked?

---

### Post by SamJosRob on 2009-06-24
Yeah, The Box says "Wireless Networking" and it's ticked.

---

### Post by keplerspeed on 2009-06-24
Excellent. So do you have a wireless network? A router? what is the network name, the encription? Is it wpa, wpa2 etc? hidden or broadcasted SSID?

Your wireless card is now working fine, you just need to connect now.

---

### Post by SamJosRob on 2009-06-24
We have a router and a wireless network. The wireless network is simply called "linksys". There is no sort of encryption, and it is broad casted.

---

### Post by keplerspeed on 2009-06-24
Left click on the network icon. If the network doesnt appear in that menu, then:

Right click on network icon, go to edit connections>wireless tab> +add. Add your network, with SSID as linksys, infrastructure mode, and security none.

However, it 'SHOULD' appear automatically..

---

### Post by SamJosRob on 2009-06-24
I right click it, then I go to "edit wireless networks". At that point, there is no wireless tab. All I can do is enter the name of the connection. The SSID option won't let me enter anything in, and no other option will let me enter anything in.

---

### Post by keplerspeed on 2009-06-24
Open a terminal and type:

```

ndiswrapper -l

```

And post the output. IT appears wireless is not working, you should have a wireless tab. This is to ensure we have the right driver.

---

### Post by SamJosRob on 2009-06-24
Output:

rt2870 : driver installed
    device (1737:0078) present

EDIT: Eh, a combo of letters/numbers formed the smiley. But both are installed and present

---

### Post by keplerspeed on 2009-06-24
Is the router turned on??

Enter this to the terminal:
```

sudo iwlist scan

```

---

### Post by philcamlin on 2009-06-24
you cant manually connect? 

i had no problems with my wireless usb from linksys :)

thats odd though linksys products are usually supported ootb if not with a little mosification

ill try to find an answer asap

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> Is the router turned on??

Enter this to the terminal:
```

sudo iwlist scan

```
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```Oh, and yes, the router is turned on. My laptop with Windows Vista on it detects the network and the router itself is clearly running.

---

### Post by keplerspeed on 2009-06-24
Wireless isnt playing nice.. Ok:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)

Read the comment..

---

### Post by philcamlin on 2009-06-24
do you have rt2870.sys too? that file you need too aparently 

[https://answers.launchpad.net/ubuntu/+question/55726](https://answers.launchpad.net/ubuntu/+question/55726)

---

### Post by keplerspeed on 2009-06-24
So what we COULD do, is remove ndiswrapper packages that we installed, then:

follow this, steps 1-6
[http://ubuntuforums.org/showthread.php?t=972060](http://ubuntuforums.org/showthread.php?t=972060)

BUT lets try philcamlin's suggestion first.

---

### Post by keplerspeed on 2009-06-24
Hmmm, but it appears that the win wireless driver has installed fine.

I would follow the ubuntu guide, as in #22... But the guide is quite messy.

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> Hmmm, but it appears that the win wireless driver has installed fine.

I would follow the ubuntu guide, as in #22... But the guide is quite messy.

I'm clueless as to how to navigate to the folder using terminal.

---

### Post by keplerspeed on 2009-06-24
So you have dowmloaded the folder and extracted it? Now in the terminal you can type:
```

ls

```
To list the the folders and contents, andL:
```

cd foldername

```
to move into the the folder, "foldername"

But you will need to install build-essential before building the driver, it is in synaptic.

---

### Post by keplerspeed on 2009-06-24
The best guide is here:
[https://answers.launchpad.net/ubuntu/+question/45440](https://answers.launchpad.net/ubuntu/+question/45440)

Here is a combination of all the guides, that should make sense:
> Open a terminal and type:
```

sudo aptitude install build-essential
sudo aptitude update
sudo aptitude remove ndiswrapper

```

Next:

Step 1 - Download the modified driver source here: [http://rapidshare.com/files/160951015/WUSB600N.tar](http://rapidshare.com/files/160951015/WUSB600N.tar)
Step 2 - Extract WUSB600N.tar to a folder, by opening in the file browser (places>home folder), right click and extract here.
Step 3 - Open a terminal and navigate to the newly created WUSB600N folder:
```

cd WUSB600N

```
Step 4 - in the terminal type:
```

sudo make

```
step 5 - then:
```

sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT2870STA
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

```

Almost done, we have to load the driver kernel module. Select again the terminal, navigate to the subfolder os/linux:
```

cd os/linux/

``` and then load the module with:

```

sudo insmod rt2870sta.ko

```

To get it running always at startup, we have to edit a file. Open it by typing in the terminal 
```

sudo gedit /etc/modules

```
then at the end of file add the line "rt2870sta" (without the quotes). Save and close.

Reboot your pc, it should then work.

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> So you have dowmloaded the folder and extracted it? Now in the terminal you can type:
```

ls

```To list the the folders and contents, andL:
```

cd foldername

```to move into the the folder, "foldername"

But you will need to install build-essential before building the driver, it is in synaptic.

I type in "ls" and get ```
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
```

I don't understand what to do next

---

### Post by keplerspeed on 2009-06-24
Where did you download the .tar to?

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> Where did you download the .tar to?

My desktop. I then extracted it to my desktop under the name "WUSB600N"

EDIT: Okay, I moved both the .tar and the extracted file to my home folder.

---

### Post by keplerspeed on 2009-06-24
ok so in the terminal type:
```

cd ~/Desktop/WUSB600N

```

Follow my guide in post #28, I have updated it. Remember to install build-essential etc (with ethernet connected. ensure you have followed all actions in post #28 )

---

### Post by SamJosRob on 2009-06-24
Okay, I make it to step 5. After step 5, I do not know how to navigate to the sub folder.

EDIT: Whoops, I skipped over a line. I make it after step 5.. I'm at the step when I have to add the line into the file. >  then at the end of file add the line "rt2870sta" (without the quotes). Save and close.

Reboot your pc, it should then work. 			 		

Which is the file?

---

### Post by keplerspeed on 2009-06-24
So type:
```

sudo gedit /etc/modules

```

A text editor should pop up.

---

### Post by SamJosRob on 2009-06-24
Yeah, I edited the file and just rebooted. Now let me see if it worked.\

EDIT: No, it did not seem to work...which leads me to believe somewhere I did something wrong.

---

### Post by keplerspeed on 2009-06-24
It should then look like this:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
# linksys usb wireless adapter module
rt2870sta

```

---

### Post by SamJosRob on 2009-06-24
Okay, I see what I did wrong, and think I fixed it. Another reboot...

---

### Post by SamJosRob on 2009-06-24
No, it did not work. So I'll try to find where I went wrong

---

### Post by keplerspeed on 2009-06-24
Firstly, did the module load? see by:
```

lsmod | grep rt2870sta

```

Also can you post your /etc/modules file here.

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> Firstly, did the module load? see by:
```

lsmod | grep rt2870sta

```

 ```
sam@Sams-Ubuntu-desktop:~$ lsmod | grep rt2870sta
rt2870sta             498772  0 
usbcore               146412  8 rt2870sta,ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

```

---

### Post by SamJosRob on 2009-06-24
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
rt2870sta
```

---

### Post by keplerspeed on 2009-06-24
It appears that you didnt remove ndiswrapper, so enter:
```

sudo aptitude remove ndiswrapper

```

Other than that it looks great. Do a reboot then see if it works.

---

### Post by SamJosRob on 2009-06-24
Okay, it's removed. Now what?

EDIT: Okay, rebooting

---

### Post by SamJosRob on 2009-06-24
No dice, it still doesn't work.

---

### Post by keplerspeed on 2009-06-24
Some explaination:

The ndiswrapper allows you to use the windows wireless driver. However this didnt work for your usb adapter.

The rt2870sta module apparently works. However, with ndiswrapper installed, the two module drivers are both installed to run the one wireless card. Obviously this is bad. We must only have one driver running, therefore removeing ndiswrapper allows the rt module to load independently for the wireless card.

Have a look at post #28. Ensure you have followed all of those in that order.

---

### Post by keplerspeed on 2009-06-24
Actually, please open a terminal and enter:

```

lsusb

```

and Post the output, so we can confirm what the wireless chipset is.

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> Actually, please open a terminal and enter:

```

lsusb

```and Post the output, so we can confirm what the wireless chipset is.
```
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 1737:0078  
Bus 001 Device 001: ID 0000:0000  

```I've followed all of the steps correctly, as far as I can tell.

---

### Post by keplerspeed on 2009-06-24
Well im stumped. It seems like people are having issues with the card:

[http://joeb454.ubuntuforums.org/showthread.php?t=928826&page=2](http://joeb454.ubuntuforums.org/showthread.php?t=928826&page=2)

[http://ubuntuforums.org/showthread.php?t=929171](http://ubuntuforums.org/showthread.php?t=929171)

Can you enter this:
```

lspci

```

---

### Post by SamJosRob on 2009-06-24
> **keplerspeed said:**
> Well im stumped. It seems like people are having issues with the card:

[http://joeb454.ubuntuforums.org/showthread.php?t=928826&page=2](http://joeb454.ubuntuforums.org/showthread.php?t=928826&page=2)

[http://ubuntuforums.org/showthread.php?t=929171](http://ubuntuforums.org/showthread.php?t=929171)

Can you enter this:
```

lspci

```
```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

```

---

### Post by keplerspeed on 2009-06-24
Did you have the wireless card plugged in? My bad, it appears usb devices do not appear as pci hardware.

---

### Post by SamJosRob on 2009-06-24
Yeah, it's plugged in.

---

### Post by keplerspeed on 2009-06-24
Most RaLink cards are fine, out of the box. However:
> Basically the problem is although the adapter uses the RT2870 chipset, the Ralink drivers don't know it yet, so you have to add the name of the adapter and change a few variables to support WPA.

From:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)

So, possibly go back to square one, and try my post #28 again.. other than that I recommend D-Link ([https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)), or any other card that works out of the box.

This is unfortunate. Most hardware is fine with linux, you just have to be a little careful. Unfortunately you card is one of the nice ones...

---

### Post by SamJosRob on 2009-06-24
What I might just do is buy a modem and a splitter, and get an Ethernet connection on the second floor of my house. Thanks for all of your help through this. Even if it doesn't work, I can give it to a friend or keep it just in case. And I learned a bit more about terminal. :)

So, this has been solved me thinks

---

### Post by keplerspeed on 2009-06-24
However, this may be much cheaper to get one of the supported out of the box usb cards, than buying a modem etc.

---

### Post by SamJosRob on 2009-06-24
Well, if I get the modem I'll be able to get an Ethernet connection with my 360 and PS3 as well. Not really needed since I have the 360 wireless adapter but I'll see some increased speed. I'll think on it, whether or not to buy the modem.

---

