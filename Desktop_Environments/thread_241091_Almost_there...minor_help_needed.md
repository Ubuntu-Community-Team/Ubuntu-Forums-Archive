---
title: "Almost there...minor help needed"
date: 2006-08-21
forum: Desktop Environments
---

### Post by beanlover on 2006-08-21
I have just moved away from XP on my laptop (again).  I want to make this move the permanant one.

I need just a little help to make everything "final":

I need the system to load the module "fuse" automatically.
I need my wifi to connect and get the IP automatically during boot.

Right now I have to do a "sudo modprobe fuse", "gksudo wifi-radar", and "sshfs blah@blah:/ /media/blah" everytime I reboot.  Would love to be able to automate these three commands so I can just start working.

I've looked around a bit and found different solutions but none that have worked for me.  I don't want to randomly try different things because that has messed me up in the past.  This is why I am asking for help directly in this case.

Thanks!

B

---

### Post by gborzi on 2006-08-21
You can automatically load the fuse module by listing it in /etc/modules, which is basically the list of modules to load at startup; as for wifi-radar, if the module is loaded and it is correctly configured it should be started at startup. I don't know for sshfs, I have never used it. If it works like nfs you need simply to put an entry in fstab.

---

### Post by beanlover on 2006-08-21
> **gborzi said:**
> You can automatically load the fuse module by listing it in /etc/modules, which is basically the list of modules to load at startup;

Thanks!

> **gborzi said:**
> as for wifi-radar, if the module is loaded and it is correctly configured it should be started at startup.

I actually don't want to use wifi-radar at boot...what I want to do is properly configure my /etc/network/interfaces so the wifi connects during boot to my AP.  I almost never take my notebook elsewhere...and if I ever do I can start wifi-radar manually to look for other APs.

Here is what is in my /etc/network/interfaces currently:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

wireless-mode Managed
wireless-essid Encrypted
wireless-key xxxxxxxxxxxx

I'm not sure what else I need in here to make it all work.


> **gborzi said:**
> I don't know for sshfs, I have never used it. If it works like nfs you need simply to put an entry in fstab.

This one I'm not too worried about...I can manually connect once I'm booted now that you helped me auto-load fuse. :)

Thanks!

---

### Post by gborzi on 2006-08-22
I'm not experienced with wireless (the AP I can use at University has a weak signal, so I prefer using the wired connection). My interfaces configuration for wlan0 is like your, besides the *wireless-mode Managed* entry. Perhaps there is a conflict between wifi-radar and the interfaces configuration. You can try to disable wifi-radar at starup > sudo update-rc.d wifi-radar remove so that only /etc/init.d/networking manages the connection.

---

