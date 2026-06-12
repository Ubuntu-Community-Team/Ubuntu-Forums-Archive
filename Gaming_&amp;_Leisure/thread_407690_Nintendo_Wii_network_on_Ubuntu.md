---
title: "Nintendo Wii network on Ubuntu"
date: 2007-04-12
forum: Gaming &amp; Leisure
---

### Post by lakersforce on 2007-04-12
Anyone who knows how to get a Nintendo Wi-Fi USB Connector to work with Wii on Ubuntu? I cant figure it out, so if someone who is wizardy enough, a guide would be appriciated.

---

### Post by Gorthus on 2007-04-12
The only operating system officially supported by the Nintendo Wi-Fi USB Connector is Microsoft Windows XP. While it may work with 2000 or Vista, I doubt it would be possible with any linux. Sorry.

---

### Post by bastiegast on 2007-04-12
> **Gorthus said:**
> The only operating system officially supported by the Nintendo Wi-Fi USB Connector is Microsoft Windows XP. While it may work with 2000 or Vista, I doubt it would be possible with any linux. Sorry.

9 Out of 10 hardwares says on the box it only officially supports MS Windows. Most of it works fine with linux.

I have no idea about this wii thing though.

---

### Post by Rizado on 2007-04-12
First of all try typing "lsusb" in a terminal, look for any interesting things, also check /proc/bus/usb/devices

I'm not familiar with the Nintendo Wi-Fi adapter but it sounds just like any Wi-Fi adapter, and I doubt they put any money into making their own stuff from scratch when there's so many chipsets already done. First thing to do with things not working is always to identify what it really is.

---

### Post by lakersforce on 2007-04-12
Ubuntu finds the device when it is plugged in, but the Wii can not find it. I guess somehow a lot of things needs to be configured proberly before it works and it is this I need help with.

> **Gorthus said:**
> The only operating system officially supported by the Nintendo Wi-Fi USB Connector is Microsoft Windows XP. While it may work with 2000 or Vista, I doubt it would be possible with any linux. Sorry.

Sorry Gorthus, but I definitely think you are wrong there. Not about the part about it only being officially supported for windows, but about the part that it is not possible with linux.

[QUOTE=Wikipedia]Although the Nintendo Wi-Fi USB Connector only officially supports Windows XP-based PCs, the card uses a common Ralink chipset which is supported on many platforms, including OpenBSD and Linux.[/QUOTE]

Question is, how to do it?

And since I am not a computer wiz-kid or a hacker it would be very nice with some human readable instructions :)

---

### Post by Rizado on 2007-04-15
Not sure about this but I think your wii is configured to use DHCP to get ip from a router or something. And the dongle software is just a DHCP server so basically your computer connected to the dongle is acting as a router to the internet. So what you need to do to get the wii working through a linux computer instead of a windows one is:

1. Getting the dongle interface working
2. Setting up a DHCP server unless you already have one (If it's possible to configure the wii manually this is not needed)
3. Configuring the firewall correctly, if you have a router I'm not sure if it's needed but if you don't you'll have to use nat, masquerading and everything to get it work like a router. Firehol can be used to do this.

Note that I'm not sure this is what you could do, or how the wii communicates but if it is, the whole wii dongle thing is a pretty ugly way of getting internet connection. You'd be better of buying a wireless access point. This way you'll never need to have your computer turned on.

---

### Post by Zeromaru on 2007-04-24
The adapter is just a Ralink RT2500 chip bundled with software to make it an access point. [This]("http://forums.afterdawn.com/thread_view.cfm/390312") contains a tutorial on making it work as a general access point (not for just Wii/DS). If someone can apply a similar technique to doing this in Linux, that'd be great, as this is one of those nagging little points keeping me from switching to Feisty full-time (that and my Radeon X1650 which I'm gonna try to trade for a GeForce 7600 GS).

---

