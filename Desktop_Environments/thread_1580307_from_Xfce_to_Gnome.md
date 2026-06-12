---
title: "from Xfce to Gnome"
date: 2010-09-23
forum: Desktop Environments
---

### Post by Samurijder on 2010-09-23
Hello everyone,

I've got an asus eee pc900, 2GB of RAM, running on xubuntu. The Xfce environment doesn't see any of the other partitions on the machine. That's why I would like to change from Xfce to Gnome.
Could anyone tell me how to do this? I've found several ways to change the other way around, but not from Xfce to Gnome.

Thanks!

Martijn

---

### Post by mcduck on 2010-09-23
There's no need to change desktop environment for reasons like that. Just configure your partitions properly and you'll see them regardless of what DE you use or if you use a DE at all. :)

Here's some guides for you:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by ronnielsen1 on 2010-09-23
You could add gnome by installing ubuntu-desktop in synaptic or by typing [COLOR=Blue]sudo apt-get install ubuntu-desktop[/COLOR] in a terminal.

---

### Post by Samurijder on 2010-09-23
> **mcduck said:**
> There's no need to change desktop environment for reasons like that. Just configure your partitions properly and you'll see them regardless of what DE you use or if you use a DE at all. :)

Here's some guides for you:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

I'm gonna give it a go. But it's weird that they're not found or mounted by default, as they are with gnome...

---

### Post by mcduck on 2010-09-23
It's not weird, really, automatic mounting isn't any system-wide thing in Linux, it's something the Gnome desktop does for you.

Actually, at least on all my systems, Gnome doesn't automatically mount any internal partitions that aren't configured in fstab, it only shows them in the menu and mounts them at the time you try to access them.

Probably same would happen in XFCE if you used Nautilus as your file manager there. (I can't say for sure, it's been ages since I've used XFCE and even Gnome didn't have this feature back then).

---

### Post by Samurijder on 2010-09-27
> **mcduck said:**
> It's not weird, really, automatic mounting isn't any system-wide thing in Linux, it's something the Gnome desktop does for you.

Actually, at least on all my systems, Gnome doesn't automatically mount any internal partitions that aren't configured in fstab, it only shows them in the menu and mounts them at the time you try to access them.

Probably same would happen in XFCE if you used Nautilus as your file manager there. (I can't say for sure, it's been ages since I've used XFCE and even Gnome didn't have this feature back then).

I guess you're right. I think I should have called it auto-detect.
After some further searching I found a solutiun on 
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)  
They've figured out the differences in packages between Gnome and Xfce an thought up a command to run.
Strange though it may sound, the EEE is actually running smoother with Gnome than on Xfce.

Thanks everybody for your advice and time,

Martijn

---

### Post by 3Miro on 2010-09-27
I had a number of issues with automount when I was using Xubuntu. The best I could figure out to do was to was to install nautilus (from Synaptic or the software center). The I would use Thunar (the XFCE manager) for regular file browsing and go to nautilus every time i wanted to mount/unmount.

---

