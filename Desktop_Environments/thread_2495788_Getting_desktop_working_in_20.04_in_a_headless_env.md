---
title: "Getting desktop working in 20.04 in a headless enviornment"
date: 2024-03-01
forum: Desktop Environments
---

### Post by matt_l2 on 2024-03-01
I have an Ubuntu 20.04 desktop machine that is going to be transferred to a remote location in a few weeks.
I have been trying to prepare it for that transfer. There are a few tasks that look like they require desktop access for (though I'd be open to command line based alternatives that work via SSH). 

I currently set up the system for automatic login to deal withe the issue that screen sharing breaks after a reboot until you log in, toggle it off and toggle it back on again.
The resulting keyring popup wasn't too intrusive so I proceeded to then testing it as a full headless system which is where I'm currently stuck.
When I connect to VNC, I get a 640x480 window with the keyring unlock popup but I can't clock on anything or type on anything. 

I've tried installing tightVNC and that hasn't worked (I couldn't get my VNC client to connect and I didn't invest any more time in it because screen sharing almost works).
I also tried RDP but I get a black screen after logging in. Again, I refocused my attention to screen sharing after that. 

My main reasons for trying to have desktop access are as second means of working with the system if the command line gets int eh way, and because I need the system to access Google Drive which I log in with via a corporate SSO and I don't see a way to do that without a GUI. 


What are my options short of a 3rd party KVM over IP solution?

---

### Post by TheFu on 2024-03-01
Never automatically setup logins to places that aren't physically locked.  There's no need.

If you use NX-based remote desktop, you'll get better security, better performance, better controls over what bandwidth is needed.  After people switch, they say it is like stepping in from the dark into the light.

NX leverages ssh, so if you have ssh already working through the firewall (hopefully on a non-standard port, only using ssh-keys or ssh-certs, never passwords, you'll find it excellent provided at least 128 Kbps, though that little bandwith can be a challenge to work, but it is possible.  I've used ISDN connections from very remote locations back to my home system and been able to tune the settings and compression to make it pretty good.  My home network only has 5 Mbps up, so it isn't exactly fast, but that's more than sufficient.

There are other options that you may not have considered, like using a SOCKS5 proxy instead of a full remote desktop. Running through a SOCKS proxy (ssh can do this), allows access to web apps inside the other network. This is handy, since it doesn't expose those webapps to the internet at all.  Of course, you can also setup a VPN server for access in either direction. Just ensure any issues with it can be handled unless you can visit the remote location in a few days to fix it.

A great way to test this stuff out is to setup everything remote on a VPS and run all the remote stuff there for a month. Do some patching. Do a major release update (those can go really wrong).  

If you can, ensure you have full console access to the system - like IPMI or a PiKVM provides.  Add that to the total package, if this is for work.  [https://noted.lol/pikvm/](https://noted.lol/pikvm/)  They did have plans publicly available and some available for about $150 + the cost of the PI.  Now it seems they've setup a Kickstarter ... which usually means long lead times.
IPMI is only available on servers with the card designed into the motherboard, so if you haven't validated that, do it ASAP.  IPMI has a long history of security failures, so if you do go that direction, never make it directly available over the internet. That isn't safe.
These are more complete solutions than remote desktops, but you seem to have decided against them.

The main problem with RDP and VNC is that they are tied to the desktop running on teh system. They aren't virtual, like NX is.  

Oh - almost forgot - NX implementations are not compatible. The commercial one is from NoMachine and has limitations.  I've never used it.  I've used 3 other implementations, but for about the last 15 yrs, it has been **x2go**.  I don't use it ever on the same LAN.  [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go) is the place to start.  Oh ... and you'll need a light DE installed, so not KDE nor Gnome.

---

### Post by MAFoElffen on 2024-03-10
Headless = Use Xorg, and i an xorg.conf file... It should include something like this
```

Section "Device"
    Identifier  "Card0"
    Driver      "nvidia"
    BusID       "PCI:5:0:0"
    [COLOR=#ff0000]Option "AllowEmptyInitialConfiguration"[/COLOR]
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    [COLOR=#ff0000]Option   "IgnoreEDID"[/COLOR]
EndSection

```
And if you want a resolution, define and set a preferred mode.

The reason for this, is that usually PC with graphics queries a monitor to see if one is connected, and what modes it can do... In headless, you tell it not to look for one. Since that info is then not queried, then you need to tell it what to use as information for that. (defined mode, and set to it)

Understood? Or do you need more information?[COLOR=#ff0000][/COLOR]

---

