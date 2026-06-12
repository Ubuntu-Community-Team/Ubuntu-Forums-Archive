---
title: "A few problems"
date: 2005-08-02
forum: Desktop Environments
---

### Post by caveman017 on 2005-08-02
Okay, i have 5.04 installed on my laptop, but i have a few problems:

The touchpad is like WAYYYY to over sensitive.. ive turned it down in the settings, but it doesnt seem to help

Battery - under XP, i can get almost 4 hours, but with linux, im down to around 2.5

WiFi.. using my intel 2200GB, i set my connection up with WEP, but upon reboot, bam nothing and i have to reconfigure it

text.. it just looks strange compared to windows, its kinda blurry (yes res is set to 1280x800)

Media Player - it doesnt work, gives me an error message

i cant acces my NTFS partition with XP on it

besides, it seems okay for my first linux thing

Laptop - Compaq Presario X1360US: Intel Pentium M 1.4GHz, 2x256MB PC2700, 60GB 4200 RPM Fusjistu, 32MB ATI Radeon 9000 Mobility, 15.4" WXGA, 8x24x10x24 DVD/CD-RW

---

### Post by odin on 2005-08-02
I'll try to take the wifi thing.First check if you jave installed wireless-tools package.If you dont installed it.After that edit your /etc/network/interfaces nad post what you have there.

It should look like:
If you have dhcp:
auto "network interface"
iface "network interface" inet dhcp
wireless-mode (here normally is managed)
wireless-essid "essid"
wireless-key your_key

If you have your IP static:

auto "network interface"
iface "network interface" inet static
address x.x.x.x
netmask x.x.x.x
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x
wireless-mode (here normally is managed)
wireless-essid "essid"
wireless-key your_key

hope this helps you.

and about accesing the partition with xp.Could you post how you try to access it?you mount the partition everytime you want? do you have an entry in /etc/fstab?

---

### Post by Lord Illidan on 2005-08-02
> and about accesing the partition with xp.Could you post how you try to access it?you mount the partition everytime you want? do you have an entry in /etc/fstab?

I doubt this will mean much to a guy who has started using Linux..

Try browsing the [Ubuntu Guide](http://www.ubuntuguide.org) for more information...

---

### Post by odin on 2005-08-02
[QUOTE=caveman017]

besides, it seems okay for my first linux thing

[/QUOTE]
:ooops: I didnt notice it...If you have any problem with the guide just post it.

---

