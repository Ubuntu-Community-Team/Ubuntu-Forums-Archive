---
title: "Default Gateway Device Issue"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Regord on 2006-09-21
Hello,

I've got a recurring issue that I can't seem to remedy.

Everytime I boot my Ubuntu machine, the default gateway is null or not selected.  This obviously prevents me from accessing the internet but I simply go to System | Administration | Networking and there is an option to select it (at the bottom of the window).  It is always blank when I launch that program but if I click on it, it comes up with eth0.  I simply click on that and press OK and I'm able to go one without other issues. 

However, every single time I reboot, I'm having to reselect this default gateway.  I know Linux is stable and can be left on for long periods of time but this is a home system and it doesn't make sense to me to leave it on when I'm not here to use it....seems awfully wasteful.  So I reboot frequently.

Any suggestions how to make eth0 my default gateway permanently??

---

### Post by Regord on 2006-09-21
To update:

when I type ifconfig I see 3 devices, eth0, lo and usb1.  I think the problem might be due to the usb1 showing up...I don't have any network devices hooked up to my usb ports.  Is there a way to get rid of this??? Perhaps that would clear up my issue....any suggestions?

---

### Post by Regord on 2006-09-22
*crickets* 

um...anybody in here? :)

---

### Post by ghettobilly on 2006-09-22
look in /etc/network/interfaces

if usb1 is listed there remove it should fix it

---

### Post by Regord on 2006-09-22
> **ghettobilly said:**
> look in /etc/network/interfaces

if usb1 is listed there remove it should fix it

Thank you for the suggestion.

usb1 was not listed anywhere in that file.  Any other suggestions?

---

### Post by ghettobilly on 2006-09-23
im not sure how to set default gateway on ubuntu/debian on redhat/fedora i could add GATEWAY=(ip of gateway) to /etc/sysconfig/network that would set that as default no matter what dhcpclient got from dhcp server
maybe someone with more experiance than i on debian could help

---

### Post by Regord on 2006-09-23
See that's the thing.  It's the gateway device of the machine, not the network and I dunno how to make eth0 the default choice.

---

### Post by Regord on 2006-09-23
Issue still not resolved...hoping someone on the Saturday crew has an idea??

---

### Post by ayoli on 2006-09-23
there is a bug report about that:
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/37841](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/37841)

---

