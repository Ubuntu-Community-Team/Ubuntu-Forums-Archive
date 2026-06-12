---
title: "Beryl with 3 Monitors / Xinerama"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by freerick on 2007-04-03
[SIZE="4"]Has anyone had any success with **setting up Beryl on a system with three monitors**?[/SIZE]

I have two NVidia 6200 cards and I'm using Xinerama to emulate one large desktop spanning all three screens, but with different resolutions and boundaries on each screen. It works like a charm, but I can't get Beryl or Compiz to work because appaprently Beryl requires the RandR extensions to be present. It is present, but it's disabled by Xinerama, since it's theoretically not needed when there is more than one monitor. If I only use two screens and switch to TwinView, thereby circumventing Xinerama, Beryl works, further corroborating the theory that the lack of the RandR extension with Xinerama is the likely cause for the problem; this has also been brought to the attention of th Beryl dev team and they said they "might offer a fix" in one of their "future releases". 

I've read reports that people have successfully set up **three screens with Beryl**. If anyone has any information on how to patch the code or other techniques I could employ to make this happen, it would be greatly appreciated.
Regards,

---

### Post by kiranlightpaw on 2007-05-04
If anyone knows how to do beryl + three monitors, I'd be interested as well. I'm currently using Xinerama that isn't Beryl-compatible but would love to get to play with it. Running three monitors on two nVidia Geforce 7600 GS PCI-Expresses.

---

### Post by freerick on 2007-05-05
yeah, I was hoping that in Feisty this problem would be addressed, especially since the Beryl package is installed by default in this distro. From what I've been able to see so far though, this bug has not been addressed, although it was stated in the changelog that the new version of Xorg has been made more compatible with composite window managers (i.e. Beryl, Compiz, etc).

---

