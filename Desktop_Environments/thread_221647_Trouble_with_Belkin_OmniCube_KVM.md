---
title: "Trouble with Belkin OmniCube KVM"
date: 2006-07-23
forum: Desktop Environments
---

### Post by mdhankins on 2006-07-23
I've got 4 boxen connected to a Belkin OmniCube, and the only one that ever has any problems with switching from one computer to the next is the one that I have tried installing Ubuntu 6.06 on.  After switching back to my Ubuntu box, the mouse freaks out.  I believe that the problem could be resolved by reloading the mouse driver/module, but it's kind of a pain to have to do this.](*,) 

This issue has been mentioned in several posts without any good suggestions for how to resolve except to buy a new KVM.  I would almost accept this answer, because my KVM is rather old (5 yrs?).  

I recently discovered that Fedora FC5 and OpenSUSE 10.1 don't have the same issue after trying them out on the same hardware (shuttle sb83g5, p4-3.4, intel915 chipset).  

Please let me know if anyone has any suggestions for how to resolve this.  I'd REALLY prefer to run Ubuntu over Fedora or SUSE.

---

### Post by nix4me on 2006-07-23
There are many posts on this forum about flaky kvm perfomance with belkin switches.

Use the search and search for kvm.

Also, you are not going to like the outcome.  Belkin kvm's simply suck for Linux.

nix4me

---

### Post by mdhankins on 2006-07-23
Thanks for the reply, but I have read through the posts.  The information in them were quite lacking.  If this problem were to exist on all other recent Linux distros, I would go forward with replacing my old Belkin KVM.  

I have installed Fedora FC5 and OpenSUSE 10.1 on the exact same hardware.  When I switch away from that computer and then back, the mouse freaks out for a second and then magically recovers.

I am having a difficult time believing that the Fedora and SUSE developers were able to figure out a way to fix this while Ubuntu decided to give up.  ](*,)

---

### Post by orb9220 on 2006-07-24
You do have a point there. 

But I had to deal with the KVM switch problems on XP only machines.

And there complaints all over the place about flaky operations with varying motherboards and KVM switches in general.

So it's not just a ubuntu problem.

---

### Post by mdhankins on 2006-07-24
I wouldn't doubt that there are people out there that have trouble with certain KVM switches and Windows XP on certain motherboards.  The worst problem that I have had on Windows is not having a scroll wheel if the system boots up while I am switched to a different PC.  

My hunch here is that when the keyboard/mouse are switched back to the Ubuntu box, some error occurs on the ps/2 ports which the mouse driver can't recover from.

---

### Post by orb9220 on 2006-07-24
Make sense since that seem to be the prob on xp machines and how they handled
the mouse and keyboard with usb ones more problematic then the older ps2 type.

---

