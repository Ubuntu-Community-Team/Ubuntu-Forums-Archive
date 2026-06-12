---
title: "Uninstalling removed USB function"
date: 2009-01-21
forum: General Help
---

### Post by wekya on 2009-01-21
Help

I was having problems with my IBM x-30 running Mint elyssa (based on Hardy) connecting to secured (mint was the only distro to work ",no WEP/unsecured, out of: FC8, debian,suse,ubuntu,kubuntu....this prism chip is old, fussy and unsupported) wirless hotspots, so took various posts suggesting WICD was "it" and uninstalled gnome network mgr and installed wicd.

During the manual uninstall of gnome network manager*GNM (duh) I lost all networking support which was needed to add wicd using synaptic. So, I downloaded the network manager to a usb, put GNM back on the IBM and it worked wired, and could smell the secured hotspot nearby OK. I then used synaptic to install wicd (correctly letting IT do the uninstall of network manager) and wicd installed fine. Once installed wicd didn't see my prism card as eth1 at all, and would not allow eth0, the wired ethernet, to connect to my network (it had been connecting OK under GNM). During the Wicd uninstall I did see a message saying something which was unnecessary couldn't be removed, sorry I don't know what exactly, but the uninstall finished successfully.

So I uninstalled wicd and now I have no USB or networking, so I can't even use the copy of gnome manger I have on my USB stick to get everything back online at least wired. I have no repositories cached locally, and this IBM has no CD/DVD ROM.

What exactly should/can I do to reestablish USB connectivity, or what step should I post here to help begin to diagnose or to fix this problem? I did try to use the recovery mode, but it also could not get network connectivity. I need detailed instructions....sorry. This sort of thing is way above my pay grade. I have no option to downlod and do a fresh install as I am in holiday in Malaysia and the net cafe won't allow it and it says it's take 10 hours to get a copy. I am going to try to dl feather linux and try to get it on a usb (pendrivelinux).

---

### Post by cariboo on 2009-01-21
You  should have networking without the network manager. try in an Applications-->Accessories-->Terminal:

```
sudo iwconfig wlan0
```

this should enable your wifi adapter, next in the same terminal type:

```
sudo dhclient wlan0
```

This should get you and ip address.

BTW I have an HP laptop with a prism chipset, it worked out of the box with Mint Elyssa. I tried WICD and it wouldn't connect with either wired or wifi.

Jim

---

### Post by wekya on 2009-01-22
Thanks, that gave me connectivity to the web and I updated myself back to where I started!

I can get online on my home net with no password, but once I'm asked for a WEP key it won't connect, it just keeps presenting the same p-word screen over and over (after I input the p-word)....who knows....do I have to hex the existing p-word (the actual thing is says is "passphrase") maybe?

---

