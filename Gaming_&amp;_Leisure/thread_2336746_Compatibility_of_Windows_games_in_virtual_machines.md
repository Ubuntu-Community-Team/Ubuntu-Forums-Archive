---
title: "Compatibility of Windows games in virtual machines"
date: 2016-09-10
forum: Gaming &amp; Leisure
---

### Post by Shiryu on 2016-09-10
We know that Wine is not perfect. So virtual machines may be an option. Old games work perfectly in a virtual machine.

While new powerful graphic cards are released, new integrated graphics cards become better. Nowadays, we can play Skyrim (DirectX 9) with integrated graphics card.
The quality of virtual machines should get better as well.

Can we play DirectX 9 games, such as Skyrim, on Windows XP in a virtual machine nowadays?
The virtual machine has to provide drivers to be installed on Windows XP as guest.

In the future, we expect to play DirectX 11 games on Windows 7 guests.

---

### Post by 1clue on 2016-09-10
While I'm not a gamer, the feature you want to mess with is PCI pass-through. Your cpu and your motherboard must support VT-d for this to work.

What this means is that your host OS does not own the video card, the VM does.

---

