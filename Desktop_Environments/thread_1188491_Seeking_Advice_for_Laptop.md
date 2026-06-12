---
title: "Seeking Advice for Laptop"
date: 2009-06-15
forum: Desktop Environments
---

### Post by mach-schnell on 2009-06-15
I'm looking for a lightweight desktop environment for my laptop that I can use to share files with a Windows machine.  Gnome is a snap to use but too heavy; Xubuntu was perfect except I couldn't connect to the Windows machine.  Does anyone know if any of the alternatives (like lxde) play nice on a local network with Windows?

Thanks for your time.

---

### Post by Jekshadow on 2009-06-15
Windows file sharing is managed by Samba, remote desktop is managed by Remote Desktop Viewer and SSH is managed by something, none of which are connected to any of the desktop environments. You should be fine with any of them. I recommend KDE or GNOME for user friendliness and if you want to have a very fast, lightweight UI, try Xfce.

---

### Post by scrooge_74 on 2009-06-15
With Xfce I think you need to manually make the icon or maybe check thunar, there is proly an option there. Being a long time since I used Xfce.

Remember Xfce is not as user friendly as Gnome or KDE, you will have to do some changes the old fashion way

---

### Post by mach-schnell on 2009-06-15
> **Jekshadow said:**
> Windows file sharing is managed by Samba, remote desktop is managed by Remote Desktop Viewer and SSH is managed by something, none of which are connected to any of the desktop environments. You should be fine with any of them. I recommend KDE or GNOME for user friendliness and if you want to have a very fast, lightweight UI, try Xfce.

Yes, I know samba manages Windows file sharing.  How I would use it to mount a Windows network in Thunar is beyond me.

I'm looking for a fast, lightweight desktop environment that can browse networks.

---

### Post by scrooge_74 on 2009-06-15
Some ideas [here]("http://forum.vectorlinux.com/index.php?topic=7817.0")

You could basically mount the drive using fstab and it should appear in thunar

[Here]("http://linux.softpedia.com/get/Desktop-Environment/Tools/Xfce-4-Mount-Plugin-24171.shtml") is a plugin for thunar to mount drives

Again, more [ideas]("http://linux.com/archive/feature/153412")

---

