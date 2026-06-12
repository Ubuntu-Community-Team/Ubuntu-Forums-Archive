---
title: "Mouse won't work through KVM switch"
date: 2005-11-28
forum: Desktop Environments
---

### Post by gnerdman on 2005-11-28
I have a Belkin Omni Cube 4-Port KVM switch and 5.10 installed on a Compaq Deskpro EN.  When I connect the mouse directly to the mouse port, it works.  If I try to use the mouse through the switch port the Ubuntu box is connected to, it doesn't move.  The same kind of box running Solaris 10 x86 works fine on the switch, as do two other systems running SuSE 9.3.  If I move the Ubuntu machine to different ports with different cables, the problem follows the box, while all other machines continue to work on all ports with all cables.  It's a generic GE scroll mouse with a PS/2 plug.  Does anyone know a fix for this problem?  Thanks!

Addendum:  dmesg says, "[4294693.266000] psmouse.c: Failed to enable mouse on isa0060/seriol"

Also, it's not this specific machine, as I get the same symptoms from my kid's PCs (also Deskpro ENs) when hooking them up to the switch.  They're running Ubuntu 5.04.

Addendum II:  Just to be certain, I switched the hard drives between the Ubuntu Deskpro and the Solaris Deskpro.  The problem followed the Ubuntu hard drive, and switch goodness followed the Solaris hard drive.  It has to be a driver issue, or something.

Addendum III:  Yep, it's a driver issue.  Mouse works fine through the switch with Solaris x86 and FreeBSD.  So I guess it's FreeBSD for me.  This is the first black mark for Linux since I started running it in the Caldera Network Desktop Preview days.  Bummer.  But the KVM thing is a show-stopper for me.  Mouse drivers are just too elementary to put up with a bad one.

---

### Post by nix4me on 2005-11-28
Belkin KVMs suck.  Plain and simple.  I have 3 of them.  The only KVM I have found that working with linux 100% is the cheap IOGear.

nix4me

---

