---
title: "Wife gone 9.04"
date: 2009-04-24
forum: General Help
---

### Post by MarcusA on 2009-04-24
Hello all, I have a dual boot Ubuntu 9.04/Vista. When I went over from vista to get some files which I wanted to put in my Ubuntu partition I suddenly wasn't connected to my wifi. When I right click on the networks which normally gives me a list of all wifi connections in the neigbourhood, I don't seem to be able to get this list of connections at all :confused:

In 8.10 I had to install different drivers (athk5 or something like that) but I didn't have any problems in Jaunty beta. Anyone have an idea?



Also how do I edit my thread title? lol

---

### Post by stucky on 2009-04-24
Sorry. Nothing to add here but wife being gone because of an upgrade is substantially different than not having wifi anymore.

---

### Post by LowSky on 2009-04-24
Your wife left you because of upgrading, sorry buddy.... j/k

right-click on the wifi icon, and choose to turn off wireless, then turn it back on, sometimes that helps.

---

### Post by MarcusA on 2009-04-24
Yeah yeah, I know lol :P

I tried turning it off and on again, but nothing happens :(

---

### Post by cubeist on 2009-04-24
If you run the hardware drivers program (system/administration/hardware drivers) does it give you an option to install a driver for your wifi?  If not, there are many tutorials for your type of wife card

---

### Post by LowSky on 2009-04-24
go to add remove look for wifi radar, sometimes that aplication works better, than gnome's built in one

---

### Post by stucky on 2009-04-24
What does iwconfig return? Does it show your adapter at all? If not you might try ```
modprobe ath5k
``` but you shouldn't need to.

---

### Post by paradigm2 on 2009-04-24
Also do

```

lspci

```

in terminal and show us the output for your wifi card, if present.  If in doubt just give us the whole thing.

---

### Post by MarcusA on 2009-04-24
iwconfig can't find anything and lspci gives me this:

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
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:06.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

---

### Post by paradigm2 on 2009-04-24
> **MarcusA said:**
> iwconfig can't find anything and lspci gives me this:


01:06.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)

This will probably be a tricky one... :(

I notice a bug was filed:

[https://bugs.launchpad.net/ubuntu/+bug/353341](https://bugs.launchpad.net/ubuntu/+bug/353341)

He claims that a clean reinstall of jaunty did the trick.

Here is a thread you might want to read:

[http://ubuntuforums.org/showthread.php?t=778726&highlight=AR5413](http://ubuntuforums.org/showthread.php?t=778726&highlight=AR5413)

Just in case (since Jaunty is a little different) what does the little wifi icon, if present, look like in the upper right-hand corner of your screen?  when you do click it, what options do you get?  Can you verify that your wireless router is working from another computer?  What settings (wpa2, wpa, wep, wpa2-enterprise, wpa2-personal, etc) does your router use (there are issues particularly with wpa2-enterprise)?

Also does SYSTEM -> Administration -> Hardware Drivers

show any drivers for your wifi?

---

### Post by MarcusA on 2009-04-24
haha, well that looks promising.. :p

I get the options:

Wired Network
disconnected
VPN Connections >

When left clicking on it, and:

Enable networking
connection information
Edit Connections
About

When right clicking on it



In hardware drivers I get 3 options:

- NVIDIA accelerated graphics driver (vers 180)    which is recommended and I use

- NVIDIA acc graph driver (vers 173)

- Alternate Atheros "madwifi" driver   I tried using this, but it doesn't change anything




My wireless works on Vista, and I don't know what settings my router has :(

---

### Post by paradigm2 on 2009-04-24
> **MarcusA said:**
> haha, well that looks promising.. :p

I get the options:

Wired Network
disconnected
VPN Connections >

When left clicking on it, and:

Enable networking
connection information
Edit Connections
About

When right clicking on it



In hardware drivers I get 3 options:

- NVIDIA accelerated graphics driver (vers 180)    which is recommended and I use

- NVIDIA acc graph driver (vers 173)

- Alternate Atheros "madwifi" driver   I tried using this, but it doesn't change anything




My wireless works on Vista, and I don't know what settings my router has :(

Click enable networking.  Then reboot.

What does it say/do now?

---

### Post by JK3mp on 2009-04-24
Yeah if networking isn't enabled that would def be the problem. & LoL @ wife joke.

---

### Post by MarcusA on 2009-04-24
It doesn't do anything, it automatically switches back to "enabled" but still no list of wifi networks :(

---

### Post by Woormy on 2009-04-24
> **LowSky said:**
> 
right-click on the wifi icon, and choose to turn off wireless, then turn it back on, sometimes that helps.

Well, you fixed it for me. Thanks!

---

### Post by MarcusA on 2009-04-24
> **Woormy said:**
> Well, you fixed it for me. Thanks!

No fair!

---

### Post by paradigm2 on 2009-04-24
> **MarcusA said:**
> It doesn't do anything, it automatically switches back to "enabled" but still no list of wifi networks :(

Well we need it to be enabled to even have a chance. :)

Right click on the icon now while the network is enabled.  Is there a "Enable Wireless" option?  If so, click it and then tell us what happens.  If not, what does it say (what options are there)?

---

### Post by MarcusA on 2009-04-24
IIt still gives me these options:

Enable networking
connection information
Edit Connections
About

Can't see a "enable wireless" option though :p

---

### Post by paradigm2 on 2009-04-24
> **MarcusA said:**
> IIt still gives me these options:

Enable networking
connection information
Edit Connections
About

Can't see a "enable wireless" option though :p
So when you click enable networking it keeps a little check box in it, right?

What do you have in

```

cat /etc/network/interfaces

```

?

---

### Post by MarcusA on 2009-04-24
I can uncheck enable networking, but when I reboot it automatically checks enable networking again.

My wired adapter is plugged in, I'm not sure but it's like an antenna for wifi connections right? :p Just asking to make sure I'm not thinking of the wrong adapter or something.

---

### Post by MarcusA on 2009-04-24
In cat /etc/network/interfaces I get:

auto lo
iface lo inet loopback

---

### Post by paradigm2 on 2009-04-24
> **MarcusA said:**
> I can uncheck enable networking, but when I reboot it automatically checks enable networking again.

My wired adapter is plugged in, I'm not sure but it's like an antenna for wifi connections right? :p Just asking to make sure I'm not thinking of the wrong adapter or something.

:lol:

Sorry I was thinking you had a wired network adapter (the type you plug in -- looks like an oversized phone jack)  I guess you don't judging from your lspci output and your /etc/network/interfaces?  if you did, I was suggesting that you plug it in to the router or such just to see if it works.

I'll have to research this a bit.  Hopefully someone else can help...

---

### Post by MarcusA on 2009-04-24
Ah, I see, I'm not very technical :p so usually I have no idea what the heck is going on with adapters, and other computer related thingies haha. I guess I'll just reinstall everything tomorrow or something. 

Thanks for your help, appreciate it!

---

### Post by paradigm2 on 2009-04-24
> **MarcusA said:**
> Ah, I see, I'm not very technical :p so usually I have no idea what the heck is going on with adapters, and other computer related thingies haha. I guess I'll just reinstall everything tomorrow or something. 

Thanks for your help, appreciate it!

That's probably a good idea if you have no strong resistance to doing so.  The one gentleman in the bug report claimed that doing a clean reinstall of Jaunty magically fixed it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/353341](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/353341)

> 

Life wrote on 2009-04-03: (permalink)

Hi! I am marking this bug as invalid. I did a reinstallation and don't have the problem anymore, must have been something I did, sorry :)



Good luck.

---

### Post by MarcusA on 2009-04-24
Would you happen to know a way to do a clean reinstall but magically keep my home folder? :D

---

### Post by unutbu on 2009-04-24
The only way to protect your home account when doing a clean install is to first move the /home directory to a separate partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then, when you do a clean install, select "Manual" (rather than "Guided") partitioning, and tell the install which partition you wish to use for the root partition, and which to use for /home. Make very sure the installer is not set to format the /home partition.

---

### Post by Wiebelhaus on 2009-04-24
Sorry we can't diagnose marital problems.

Good luck , I hope you two work it out.

---

### Post by stucky on 2009-04-25
Did you try ```
 # modprobe ath5k
```?

---

### Post by MarcusA on 2009-04-25
I did, it gave me errors, dah well. I reinstalled and it works fine now :p Let's hope it stays this way..

---

