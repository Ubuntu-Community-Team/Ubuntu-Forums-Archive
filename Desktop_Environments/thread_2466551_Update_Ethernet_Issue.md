---
title: "Update Ethernet Issue"
date: 2021-08-30
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-08-30
Folks,

Asking this on behalf of a friend who is having issues and I am trying to assist

He is running Ubunta-Mate 20:04.  It is a new Desktop type setup with ethernet connection.  All working fine on kernel 5.4.0-65 but when he did an apt update && upgrade his network adapter does not show.

ifconfig -a does not show anything.  we have tried restarting network-manager.service and networking.service.  Appreciate the latter service requires an entry in /etc/network/interfaces which we have also tried.

To add to confusion with interface entries is Ubuntu's renaming of adaptors, initially we tried [COLOR=var(--black-800)][FONT=var(--ff-mono)]iface eth0 inet dhcp  - as that didn't work we tried enp1s0 which is how my machine shows it.  That didn't work but strangely, when he booted back with kernel 5.4.0-65 it seems his NIC shows as enp4s0.  Anyway, we then tried enp4s0 in the network/interfaces file and still nothing.

I am not sure what to suggest to him now so any ideas would be appreciated.

Geoff

[/FONT][/COLOR]

---

### Post by Geoff_Lane on 2021-09-12
Just in case anyone else experiences similar issues through quite a bit of trial, error, searching and experimenting it seems for some reason when the kernel was updated the following package **does not** get installed;

linux-modules-extra<version>

This was installed manually using synaptic and adaptor and network now working perfectly.

Geoff

---

### Post by TheFu on 2021-09-12
In 20.04, both ifconfig and /etc/network/interfaces are deprecated.
Use **ip** and **netplan**.

---

### Post by Geoff_Lane on 2021-09-12
> **TheFu said:**
> In 20.04, both ifconfig and /etc/network/interfaces are deprecated.
Use **ip** and **netplan**.

As mentioned in original post it was a friend's machine so any advice was via phone.  I did get him to check /etc/netplan and what appeared to be the correct configuration yaml file was there, seemed to be configured correctly for Network-Manager.

On my version of Ubuntu the linux-modules-extra<version> was installed correctly, on his an older version was installed but not the one matching his kernel, hence, if he booted using the old kernel all worked, latest kernel and no network.

Anyway, as the old saying goes, there's more than one way to skin a cat (why anyone would want to skin a cat I don't know) and there is more than one way to solve Linux issues :cool:

Geoff

---

