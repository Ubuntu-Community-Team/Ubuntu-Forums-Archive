---
title: "ndiswrapper problems"
date: 2006-01-17
forum: General Help
---

### Post by cborge on 2006-01-17
Hi.
I'm following this how to:
[http://www.ubuntuforums.org/showthread.php?t=108060&highlight=wlan+problems](http://www.ubuntuforums.org/showthread.php?t=108060&highlight=wlan+problems)

I have installed ndiswrapper 1.7 and downloaded my wlan driver

I have done this:
$ sudo ndiswrapper -i /home/whateveryourloginnameis/AR/bcmwl5a.inf

But when I try the next step:
$ sudo modprobe ndiswrapper
I get an error. It says:
> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/misc/ndiswrapper.ko) Invalid argument

sudo ndiswrapper -l gives:
> Installed ndis drivers:
bcmwl5a driver present

But I guess that I need  the $ sudo modprobe ndiswrapper to work before I can get my wireless to work ?


Anyone? Please!:???:

---

### Post by Czar on 2006-01-17
I'm not sure why/who told you to modprobe, but I believe that's un-needed.  After installing the .inf driver;

```
sudo ndiswrapper -m
sudo ndiswrapper -hotplug
sudo ndiswrapper -l
```

---

### Post by otake-tux on 2006-01-17
Use the ndiswrapper in the repositories.  It is my experience that it works better.  When I was using 1.7 it gave me troubles too.

Just get rid of that ndiswrapper 1.7, open synaptic search for ndiswrapper. Install it then ndiswrapper -i driver.inf.

modprobe ndsiwrapper it to see that it works, open network_admin and activate wlan0. Test to see if you are connected.

good luck.

---

### Post by cborge on 2006-01-17
OK thanks, but:

What do I do to remove the ndiswrapper-1.7 ?

---

### Post by az on 2006-01-17
[QUOTE=cborge]OK thanks, but:

What do I do to remove the ndiswrapper-1.7 ?[/QUOTE]
Go to the source directory you used to install it and run

make uninstall

You will need to reboot to get rid of the module if it is loaded.  Before you reboot, it is a good ides to reinstall your kernel in case the ndiswrapper module has been deleted (I doubt it)

sudo apt-get install --reinstall linux-image-2.6.12-10whatever your version)

---

