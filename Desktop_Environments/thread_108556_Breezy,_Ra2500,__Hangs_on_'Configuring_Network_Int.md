---
title: "Breezy, Ra2500,  Hangs on 'Configuring Network Interface'"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Who on 2005-12-26
Hi,
I did a fresh install of Breezy on a 500Mhz P3, with a CNet 802.11G card using a RaLink Ra2500 chipset. This model of card card works on my computer, but does take a long time to get past the 'Congiguring Network Interface' stage. This PC (My brother's) does not get past this stage at all. In recovery mode the final stage I see before it hangs is: "NET: Registered Protocol Family 17", and the step before that it disables IRQ 11...

It doesn't hang _completely_ because it still responds to SysReq commands (but after two hours it still wont finish booting)

Crucially, this install booted fine before I had 'Activated' the card using Gnome Network Manager'. We are using WEP with a hidden SSID. When I put in all the information originally (WEP KEY, SSID) (befire rebooting) I couldn't ping the router, so I think it is likely the setup is wrong - perhaps a mistyped WEP key or something - but I thought a reboot wouldn't cause a problem,so I tried that first - perhaps ann error :P. before rebooting iwconfig showed a correct SSID and a 'connection speed (between 32 and 48Mbps), but zero activity - bytes sent/recieved. which seemed to suggest the device thought itr was connected but nothing else did....!? Would iwconfig show that if the WEP key was wrong? lo was the default netwrok device originally. even after I had activated Ra0 (the wireless card) it wasn't selectable in the network status panel applet - I don't know what that indicates, but it may help...)

The position I am in is this: I don't know whether this _exact_ card is faulty or not, it was a christmas present to my brother. I know an identical card works on my PC, but I use WPA at my house so I installed the RaConfig 2500 software.
[B]
I want to 'unconfigure' the network somehow without booting -I.E using a live CD, so I can boot and reconfigure from there - as that seems to me to be the only option. I don't know how to do that though, can someone help? another option would be a bios tweak or two, if anyone knows of any settings that may cause this...?[/B]

Any help would be greatly appreciated

Who (and his borther :P)

---

### Post by sciurus on 2005-12-26
Can you hit ctrl-c while booting to stop configuring network interfaces and continue loading?

---

### Post by Tiede on 2006-01-04
I have the same problem with an Acer 3009WLCi laptop... It hangs at configuring network interfaces (even Caps locks won't come on).... If I ctrl+c at before it locks up, I can access gdm and all, but then I cannot go on the internet, even though network manager says that I am connected with a 100% signal level.
I also want to say that before I installed network manager, my system did not lock up at network configuration, although it did stay there for about 15 to 30 seconds...
Also, it seems that if I am not near a wireless hotspot, than the configuration does not lock up but lingers 3 full minutes before letting the rest of the process happen...
Is the problem related to Network Manager? Is there any way I can test it?
Any help would be greatly appreciated. (I cannot stand looking at that green start button any longer. Please, help me go back to my linux boxen!)

---

### Post by carlosqueso on 2006-01-04
Network Manager gave me problems with a D-Link DWL-650 card.  Uninstalling it fixed the problems....I'd test if it is the problem by simply uninstalling network manager and seeing if it fixes it.  If it doesn't solve the problem, you can always reinstall.

---

