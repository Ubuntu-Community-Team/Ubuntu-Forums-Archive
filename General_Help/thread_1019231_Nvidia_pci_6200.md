---
title: "Nvidia pci 6200"
date: 2008-12-22
forum: General Help
---

### Post by sa89bu on 2008-12-22
Installed a nvidia pci 6200 geforce card in ubuntu 8.10 downlaoded the 177 drivers from the package manger, activated the drive though the hardware drivers rebooted and boot menu freezes or before login window will freeze.
i have a onbaord intel card that the bios will not let me disable dunno if thats teh problem or what any would be great

---

### Post by CatKiller on 2008-12-23
You shouldn't have any problems with the 6200. I've got one of those, and it's always been fine.

> **sa89bu said:**
> boot menu freezes or before login window will freeze.

When you say "boot menu", do you mean the GRUB menu? The driver hasn't loaded by that point, which leads me to suspect a hardware problem. Is the card (and any other cards) seated properly? Have you checked your memory? That kind of thing.

---

### Post by sa89bu on 2008-12-23
everything is seated right. its not the ram i've tested it on the same setup and still did it but i do get this error rc-default main process (1077) terminated with status 255

---

### Post by sa89bu on 2008-12-23
pretty much the same probelm as this guy [http://ubuntuforums.org/showthread.php?t=402863](http://ubuntuforums.org/showthread.php?t=402863)

---

### Post by CatKiller on 2008-12-23
There is a bug [reported on Luanchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229753") where someone has the same symptoms as you. No solution though, unfortunately.

Google says that [this page]("http://backports.ubuntuforums.com/showthread.php?p=5534796") has someone with the same problem who's marked the thread as solved, but that site doesn't seem to be working today, and Google's cache won't let me see the second page to see what the solution was.

A number of proposed solutions have involved changing the kernel options for things like APIC and Local APIC, but I haven't managed to find anyone posting a solution that works. You could try those, or changing the IRQ settings in the BIOS to see if you could get the boot-up hardware detection to successfully complete.

---

### Post by sa89bu on 2008-12-23
would it matter if i use a pci raiser card?

---

### Post by CatKiller on 2008-12-23
> **sa89bu said:**
> would it matter if i use a pci raiser card?

I don't think so. You could try running it with the case off to bypass the riser card, to see if it changes anything.

---

### Post by sa89bu on 2008-12-23
got it to work with fordora 10

---

### Post by CatKiller on 2008-12-23
> **sa89bu said:**
> got it to work with fordora 10

Well, that's a start :)

As far as I know, Fedora 10 and Ubuntu 8.10 use the same kernel version. Did you happen to notice if there are any differences in the kernel options in GRUB?

Of course, if you're happy with Fedora 10 then I don't suppose it matters, except if you wanted to help someone else with the same problem.

---

### Post by sa89bu on 2008-12-24
i would rather have ubuntu then fedora and yeah they are the same kernals

---

