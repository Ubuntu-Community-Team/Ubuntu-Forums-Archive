---
title: "The Dreaded &quot;Checking Battery State&quot; message"
date: 2006-01-14
forum: General Help
---

### Post by underpope on 2006-01-14
Brand new Kubuntu install on my HP Pavilion zd8000 laptop with an ATI Radeon m300 video card.  Fedora Core 3 ran just fine on this laptop, but Kubuntu won't run.  The install went fine until the last stage, where it bombed trying to start X.  When I rebooted, it got as far as:

* Checking battery state... [ ok ]

and then it hangs.

I've seen a number of posts about this issue, but they all had to do with NVidia drivers.  Unfortunately, this machine runs ATI, not NVidia.

I have Kubuntu 5.10 running just fine on my desktop and on another laptop, and I love it; much smoother and more stable than Fedora.  But I'm stuck at this point on this laptop, and would really appreciate some help.

---

### Post by underpope on 2006-01-14
Bump.  This is an urgent matter.

---

### Post by underpope on 2006-01-14
Further attempts.  I've tried all of the options listed on the "Diagnosing IRQ conflicts" at

[https://wiki.ubuntu.com/DebuggingIRQProblems?highlight=%28irq%29](https://wiki.ubuntu.com/DebuggingIRQProblems?highlight=%28irq%29)

I've also checked my computers BIOS settings to see if I could find an IRQ setting there, but there is none.  I disabled hyperthreading since I've seen that be an issue on other computers, but that did not help.

I'm ready to dump Kubuntu on this machine and revert back to Fedora which, in spite of its problems, at least worked on this computer.

---

### Post by Tuf on 2006-01-14
Can't say I blame you. I have been trying to find a solution for ATI card for a couple of weeks now.  I am about to reach the conclusion that there is no solution in Kubuntu. I am going to try Gentoo it seems work well from the Live CD and there has  been some reasonable success on their how to's.

I can honestly say I like Windows more now than I ever have :/

---

### Post by debernardis on 2006-01-14
By no means I have the slightest idea of how it worked to fix several problems on my hp zv6278ea pavilion laptop, but before turning back to windows try to boot with the following magic spell:
```
acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq
```

More details on [this]("http://www.ubuntuforums.org/showthread.php?p=560483") thread.

Also, might be that when it does not go on in installing and stops in a text-mode console, you have to edit /etc/X11/xorg.conf adding  '**Option "NoAccel"**', like in 

```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	Option	    "NoAccel"
	BusID       "PCI:1:5:0"
EndSection
```

(your graphics adapter won't be an Xpress 200M, but the trick could work)

---

### Post by Sp@z on 2006-01-14
I had this problem as well. I solved the problem by using ctrl + alt+ F1 to bring me in to tty1 and ran fsck maunally. I am not sure what it did, but I once was ready to toss Kubuntu to the wayside over this issue.............

---

### Post by underpope on 2006-01-14
> 
```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	Option	    "NoAccel"
	BusID       "PCI:1:5:0"
EndSection
```

(your graphics adapter won't be an Xpress 200M, but the trick could work)

Awesome!  That seems to have done the trick!  I booted in to KDE, then ran sudo dpkg-reconfigure xserver xconf to get the resolution right, then edited xorg.conf manually to re-add the "NoAccel" option.

Thanks!  I owe you a beer.

---

