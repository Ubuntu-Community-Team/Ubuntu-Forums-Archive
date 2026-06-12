---
title: "Is the network manager in KDE4.4 functional?"
date: 2010-01-14
forum: Desktop Environments
---

### Post by Kimm on 2010-01-14
I've had issues with the network manager bundled with KDE4 for a long time (cant connect to wireless or VPN networks, so I have to use the gnome network management applet in KDE to get networking on my laptop...)

Has anyone here tried the 4.4 RC/Beta and noticed any fixes for it? Its a known bug, which has been around for quite a while now.

---

### Post by Zorael on 2010-01-14
I've never really had any issues with it, not in 4.3 nor in 4.4 (betas/rc1). I'm mainly connecting to WPA2 and the occasional WEP networks.

I do remember hearing something about mobile broadband not working in 4.4rc1 though, but there's supposedly [a workaround](https://wiki.ubuntu.com/knetworkmanager/mobilebroadband).

---

### Post by paulsomm on 2010-06-07
bump...I have the same issue.  I originally thought it was because I'd some leftover bits of gnome after running the kubuntu-desktop install to switch to kubuntu, but now I've just installed kubuntu 10.04 from scratch and activated my restricted drivers and still cannot get kde's network-manager to connect to my wireless.

Gnome's works perfectly if I install it.

My access points are both WPA2-Personal, if that makes a difference (haven't tried open or WEP)...

---

### Post by dreamsR4living on 2010-07-30
I have the same problem, which is one of the main reasons (the other is gtk apps being ugly) why I don't even think about switching to KDE. Gnome is working fine with my WPA2 wireless connection, but KDE only seems to be working with a LAN cable, which I don't have.

---

### Post by Zorael on 2010-07-31
> **dreamsR4living said:**
> (the other is gtk apps being ugly)

If this happens you might want to try installing **kubuntu-default-settings** and **kcm-gtk**, then enter System Settings -> Appearance -> GTK+ Appearance and make sure it's set to theme GTK apps as to fit Oxygen looks. The drawback is that you also get defaulted to the Kubuntu startup splash (and probably cursor theme), but that's easily changed.

As for the network manager, I've been running 4.5rcs and the plasma widget seems to be coming along nicely. It (or rather, the networking kded module) could still use a button to proactively scan for new networks, though. It can be a bit slow on the uptake sometimes.

---

