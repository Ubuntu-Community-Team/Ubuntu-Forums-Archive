---
title: "Ubuntu Feisty + Beryl on Vista with VMware"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by Fewleftstanding on 2007-06-12
Hi everyone,

I've posted on this forum a few times before but forgot my username. 

I recently purchased a Dell Inspiron E1505 (6400) laptop and am running Vista. My graphics card is a ATI X1400, and I have 2 GB ram.

I've installed VMware and have installed Ubuntu Feisty as a guest. I want to run beryl on Ubuntu, but I can't see to make it work. I installed beryl, but when I launch it, the window resizes and it logs me out. 

I'm not sure what to do, I've been googling this all afternoon.

Any help would be appreciated.

Thanks guys

---

### Post by el_poderoso on 2007-06-12
Personally, I would switch to Linux as your host and Vista as your guest (assuming you only use Vista occasionally). Out of the box, you'll have Vista without some of the cool, but not mission critical features (at least that has been my experience with XP) and some usb devices that will need to be "encouraged" to work.

If you use Vista most often and the only thing missing in vmware is beryl ... live without the eye candy and perhaps vmware will eventually support beryl (still a beta feature).

With XP running in vmware, I get no sound and I cannot get Palm Desktop to work. USB devices such as usb memory sticks, scanners, etc can be hit or miss. I use these devices easily in Ubuntu, so I have not been motivated to figure it out. The community site for vmware is long on questions and short on answers.

---

### Post by derred on 2007-06-16
Actually the problem is not with beryl but with the way that virtual machines are handled today. It is a sad but agreed upon fact that you can only use a 3d card with one OS at a time so the guest system is stuck with only an emulation of one with no 3d support.
I hope this explains the problem, now if only I could fix it :)

---

### Post by dannymichel on 2007-06-24
I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

---

### Post by jarocooke on 2007-06-24
> **dannymichel said:**
> I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

I would try using InnoTek Virtual Box if I were you.

I have installed Windows XP on it and it seems to work fine (though the only thing I have used it for really is downloading MP3s (no DRM) from iTunes).

---

### Post by dannymichel on 2007-06-24
> **jarocooke said:**
> I would try using InnoTek Virtual Box if I were you.

I have installed Windows XP on it and it seems to work fine (though the only thing I have used it for really is downloading MP3s (no DRM) from iTunes).
I can't get my LAN working with VirtualBox.
I'm on a college campus.

---

### Post by Tethtibis on 2007-06-26
oddly, video cards can only be "accessed by one OS at a time, it is due to their data bit restriction, the controller for the device can only look one direction at a time, sorry, but i don't think that will be fixed any time soon, because there is no real demand to change the hardware arcitecture any time soon.

---

