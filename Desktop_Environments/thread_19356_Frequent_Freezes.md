---
title: "Frequent Freezes"
date: 2005-03-11
forum: Desktop Environments
---

### Post by Napper on 2005-03-11
Hi there,

    two month ago or so I fell in love with Ubuntu and the Gnome Desktop (after reading an article about spatial navigation). While this is a great distro in terms of design and packaging I must say it hadn't been working out for me very well at all. Three words: Frequent system freezes. Now this is completely new to me in Linux, where I have seen applications crash and crash and crash but never an entire system, that required me to plug the power cable, so to speak. So, notorious an updater that I am I tried Hoary, and that didn't help very much. So I started observing: when does it freeze. For a while I thought it was the power management, then I thought a memory leak was causing my computer to die but to be honest: I haven't quite figured it out yet. Yet I am a bit reluctant to go back to Mandrake so I will start one last attempt to get this system running the way I know Linux systems to run: stabely. Here my question: Is there a sort of log of what exactly happens when to the computer, you know, where I could start getting ideas of what might be the problem? I have an IBM ThinkCenter, not the oddest of hardware, I believe, so I doubt that the hardware is the problem (Mandy ran rather well.) Where can I start? How can I get Ubuntu fixed? Do I need to wait for Hoary stable and completely reinstall? Again?

Kind regards,

Napper

---

### Post by rmjokers on 2005-03-11
If your system is freezing completely, then you probably have a problem with your video driver in X or with the kernel.  First, I would search and see if others are having similar problems with Ubuntu that have the same video card setup as you.  Next, you can try to build your own kernel and then remove drivers until the problem goes away (process of elimination).  Third, you could take a look at the /var/log/messages file and see if there is any information in there after a system freeze.

---

### Post by tnt on 2005-03-12
I am using ubuntu warty on a desktop. I have the same problem about ubuntu freezing up. IT SUCKS.  I found out that before it freezes, I recieve a message saying "IRQ #11 nobody cared", then it disabled IRQ #11. Before that messages in /var/log/messages and /var/log/kernel.log   ACPI was enabling IRQ #11.  So it seems to me that something is wrong with ACPI.  So I dig around a bit longer and found out that IRQ #11 is not only use by my wireless card,  other devices use it too.  My Ati 9600 driver use it, my usb driver use it, and another device which I forgot the name at the moment.  Anyhow,  I tried to disable ACPI but it doesn't work.  A friend of mine told me to upgrade to Hoary but I didnt' have time to do it yet.  There is a patch for ACPI but I don't know how to run it =).   

If any one knows how to solve that problem, let me know =) 

Other information, I have VIA mother board Pentium 4 CPU, ati 9600 graphic card,  WMP54G v4 linksys wireless card.

---

### Post by bryan986 on 2005-03-17
I have had 4 total lock ups in hoary today (requiring a manual restart), and I have no clue why, they were just at completely random times, this is really sad too because my windows xp ran for weeks without a single lockup or crash

---

### Post by valadil on 2005-03-17
I had quite a few freezes too until I got rid of my swap.  I don't advise this unless you know what you're doing (and thats why I'm not gonna say how I disabled swap) but if you're harddrive light is going nuts when the rest of your machine is locked up, theres a good chance swap is involved.  Also keep in mind that you need quite a bit of ram if you're going to go without swap.  I've got a gig, so my system runs fine without swap, but I couldn't give you numbers for where you'd start to need swap or more ram.

---

### Post by vasdee on 2005-07-10
i had similar problems with Mandrake 10 a while back and now with Hoary. I don't know if my problem stems from me using a Dell Laptop or not,  but basically my freezing problem occurs randomly after i make the switch from AC to battery power and vice versa. 

I dug up the old mandrake solution and tried it with hoary and so far so good. 
It just requires appending a few boot params to grub. (/boot/grub/menu.lst)

```

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash pci=bios idle=halt noapm nolapic noapic
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
```

The fix lies with the "noapm nolapic noapic" args. Its been a couple days of switching between battery / AC power and i haven't had any freeze ups.

---

### Post by Midget on 2005-10-06
is it a random-freeze, or a freeze-when-you-pull-the-power-out (aka run on battery)?

---

