---
title: "wifi not autostarting. kcmwifi problem?  conflict?"
date: 2005-12-31
forum: Desktop Environments
---

### Post by Vetto on 2005-12-31
I am running KDE3.5 and cvs madwifi drivers for a pcmcia netgear WG511T card.
  I have configured my interfaces file with the essid and key and whatnot, but when the system boots it hangs at "configuring network interfaces" and when it fails and finally boots, all I have to do is open the kcmwifi module in kcontrol and "activate" the saved configuration.  Then a simple "dhclient ath0" gets me an address and I'm cooking with gas.

Why is this not autostarting, does the system use a dfferent startup file other than the standard interfaces file since I configured the card with the control module?  If so, where is that file and why is it not loading at startup?

(for new readers, this thread is forked from another...quick and dirty background is that the card is not autostarting and fixing the interfaces file is helping.)

Last post was [here]("http://www.ubuntuforums.org/showthread.php?p=617210#post617210")
> 
[QUOTE=pugs]I would try setting your wireless channel in the interfaces file.  It seems that when you run wlanconfig before kcmwifi ath0 is using a different channel at the time then it is after you run kcmwifi.

ok, now i am on the correct channel and ap...but i cannot get an ip (dhcp).

Here is the differences in the pre kcmwifi and post kcmwifi:

before:```
 Encryption key:9B51-0DF0-F8   Security mode:restricted
```

After:```
Encryption key:9B51-0DF0-F8 [4]   Security mode:restricted

```

In the ap, i have 4 keys and i am using key 4..thus the [4] after the key in the post-kcmwifi iwconfig.  is this relevant?  After running kcmwifi I obviously can get an IP, but still not before.
[/QUOTE]

---

### Post by Lambert on 2005-12-31
If you're using key 4 then it is important

change your wireless-key entry in the interfaces file to this.

wireless-key4 xxxxxx
wireless-defaultkey 4

---

### Post by Vetto on 2005-12-31
OK, my interfaces file now looks like this:

```
iface ath0 inet dhcp
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
wireless-key4 9B510DF0F8
wireless-defaultkey 4
wireless-essid AcmeRockets
wireless-mode managed
wireless_channel 11
 auto ath0
```

(I changed the key after posting the last time :)  )

Will reboot and see what happens.

---

### Post by Vetto on 2005-12-31
:KS :KS :KS 

success!

Thanks Pugs and the almighty Lambert.

---

### Post by pugs on 2006-01-01
Yah, I was only using 1 key in my router.  I dont bother switching.  I dont know why I use any security anyway....I have no neighbors close enough to snoop onto my network anyway.

I know it took me a while to get my router set in such a way that linux even could find it for some reason.  I have a D-Link DI-624 and with the latest firmware there are a crapload of options.  It even does WPA2 or whatever now.  Not that I have gotten that working though :(

Glad you figured it out:D

---

### Post by Vetto on 2006-01-01
I know that wep is not a security method really, but not using anything is reckless.

I think you can transmit and recieve on different keys, that helps some...WPA is my next hurdle.  (gotta get a router that supports it)

---

### Post by Joe Public on 2006-01-07
I'm hoping someone can help me. This is going to be a long post, so bear with me.

I'm pretty much having the same problem as Vetto with the same hardware. I've got a WG511T PCMCIA card which i'm trying to use in an old laptop. 

Under Gnome the card was detected and installed without a worry. I even had WPA working without a hitch. But i'm a sucker for eye-candy and so i did a fresh install of Kubuntu (i also had some problems with some of the software in Gnome not working properly and issues with Samba). Kubuntu works fine except for this issue with this pcmcia card.

I've followed the guides to the letter with the exception of this:
> sudo apt-get --purge linux-restricted-modules-`uname -r`

This has never worked for me. I get an error saying 
> E: Invalid operation linux-restricted-modules-2.6.12-10-386


However, before moving on to setting up the wireless PCMCIA card, i've always updated KDE to 3.5 because i believe the Kubuntu install has KDE 3.5 RC1 as default.(?) So perhaps this is why the 'sudo apt-get --purge, etc, etc' command doesn't work?

Anyway, i proceed with the rest of the process and after i initially install madwifi-ng, all is good. I can run **modprobe ath_pci** and everything's fine. The wireless card starts if i type **ifconfig ath0 up** and the lights bounce around looking for an access point. But the problem is as soon as i restart, the computer refuses to even accept there's a card in the slot:

> root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


After the reboot, my issue is essentially this: -

> root@ubuntu:~# modprobe ath_pci
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.12-10-386/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.12-10-386/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Dmesg says this:
> [4296487.871000] ath_rate_sample: disagrees about version of symbol ath_hal_computetxtime
[4296487.871000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[4296487.878000] ath_pci: Unknown symbol ath_rate_tx_complete
[4296487.878000] ath_pci: disagrees about version of symbol _ath_hal_attach
[4296487.878000] ath_pci: Unknown symbol _ath_hal_attach
[4296487.879000] ath_pci: Unknown symbol ath_rate_attach
[4296487.880000] ath_pci: Unknown symbol ath_rate_newassoc
[4296487.880000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[4296487.880000] ath_pci: Unknown symbol ath_hal_computetxtime
[4296487.881000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[4296487.882000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[4296487.882000] ath_pci: disagrees about version of symbol ath_hal_detach
[4296487.882000] ath_pci: Unknown symbol ath_hal_detach
[4296487.884000] ath_pci: Unknown symbol ath_rate_node_cleanup
[4296487.884000] ath_pci: Unknown symbol ath_rate_detach
[4296487.885000] ath_pci: Unknown symbol ath_rate_node_init
[4296487.886000] ath_pci: Unknown symbol ath_rate_findrate
[4296487.886000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[4296487.886000] ath_pci: Unknown symbol ath_hal_init_channels
[4296487.887000] ath_pci: Unknown symbol ath_rate_newstate
[4296487.887000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4296487.887000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[4296487.887000] ath_pci: Unknown symbol ath_hal_getwirelessmodes


It happens every time after i reboot - there is no ath0 interface at all when i type iwconfig.

I've edited my /etc/network/interfaces file to include the 'auto ath0' command and/or the 'map ath0' command and it still happens either way. I've also made sure i include the 'wlanconfig ath0 create wlandev wifi0 wlanmode sta' command in the /etc/network/interfaces file too.

I've also edited /etc/modules and added 'ath_pci' at the end (without the inverted commas).

So, the things i think it *might* be are:
1) I update and install kde 3.5 which doesn't allow me to do the - sudo apt-get --purge linux-restricted-modules-`uname -r` - command before moving on to installing and configuring madwifi-ng

2) I'm also using a hotpluggable USB network card in order to connect to the internet to get things like sharutils, madwifi etc. (the laptop doesn't have a native network connection) and that's causing havoc on the reboot when it's attempting to startup the hotpluggable subsystem because there's some kind of issue there between the hotpluggable pcmcia wireless card and the hotpluggable USB network card. So i was wondering whether the ifupdown command should maybe be a part of my /etc/network/interfaces file somehow?

Any help anyone can offer on this would be greatly appreciated. This is driving me bonkers. Thanks. :)

---

### Post by Vetto on 2006-01-07
I would post this question in the MADWIFI thread...seems you have been there since you quoted commands from the instructions there...:) 

Once the drivers are loading correctly and you have an ath0 and wifi0 interface then you can move on to configuring them.

I did notice that if the /etc/network/interfaces file was misconfigured that the ath0 interface would not come up on reboot ...and in fact some setting there caused the card to not come on at all and no command that I knew could bring it up (no ath0 or wifi0 found when I ran ifconfig)

Apparently as you might have read above, some pcmcia card start with hotplug ("map ath0" in the interfaces file)...this completely disabled my card.  To start my card, I had to treat it like a normal interface...here is the complete interfaces file that I am using (key edited)

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface ath0 inet dhcp
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
wireless-key4 xxxxxxxxxx
wireless-defaultkey 4
wireless-essid AcmeRockets
wireless-mode managed
wireless_channel 11
 auto ath0

# iface eth0 inet dhcp

# auto eth0


---

### Post by Joe Public on 2006-01-07
Thanks for the reply Vetto. :)

Unfortunately, i seem to have the same problem with all variations of my /etc/network/interfaces file. I've tried the 'auto ath0' command and the 'map ath0' command at different times and always ended up with the pcmcia card sitting there blinking like some forlorn beacon - seemingly with power but not recognised by the system.

One thing i didn't try was moving the 'iface eth0, etc' details to *after* the details of the ath0 interface in the /etc/network/interfaces file, like i notice you have. It seems like it'd be a trivial change but i'm starting to discover that the devil's in the details.

In any case, i've gone running back to Ubuntu and Gnome with my tail between my legs for the time being. And good old Gnome detected the card and allowed me to install and configure WPA without an issue. I did discover that the USB network card still caused a few problems under Gnome, so perhaps that was partly the cause of my problems using Kubuntu.

So now i'm going to tempt fate and install the Kubuntu desktop after i've configured my Ubuntu and Gnome to work and see what happens. Cheers. :)

---

### Post by Vetto on 2006-01-07
KDE is more powerful and customizable...but like the gnome development team say, "gnome just works".

Now having said that, I have that card, and am running kubuntu 5.10 with KDE3.5.  I successfully have cvs versions of the madwifi drivers, not the restricted ones that come with kubuntu.

I am not that smart in this, all I know is that mine works and therefore we know that it is possible.  If someone smarter that both of us can help, together we can get yours working also.

---

### Post by pugs on 2006-01-08
Hey Joe...you say that the ath0 doesnt even exist.  I am sure you probably tried this, but do you have this in your interfaces file?

pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta

That sets up the ath0 interface...before you do that, it doesnt exist.  The madwifi-ng drivers let you create multiple interfaces running on the same card so in theory I guess you could use the card as an access point for other computers as well as a a stand alone device for the laptop and could make for some pretty complex network setups.

---

### Post by nigerag on 2006-01-10
Can anybody tell me, what is so special about Ubuntu/Kubuntu 5.10 that wireless adapter does not work. The system recognizes adapter properly but can not lease any IP addresses. I do not have that problem with Ubuntu/Kubuntu 5.04.
My adapter is NETGEAR WG511T
Thank you for any clue.

---

