---
title: "Ubuntu/Kubuntu NOT 'just working'"
date: 2005-07-27
forum: Desktop Environments
---

### Post by nwjsmith on 2005-07-27
I have a machine running an AMD Athlon 64 3200+, and my motherboard has an integrated ATI Radeon Xpress x200.

During the Ubuntu amd64 live CD boot, at the ubuntu splash screen, the computer locks up (with no mouse or keyboard functionality).

Also, during the kubuntu amd64 live CD boot, it appears X.org loads fine, but it locks up not much after the background from KDE appears.

Any help would be great.

---

### Post by aggiechemist on 2005-07-27
I had almost this exact same problem, and I discovered that I had jarred the IDE cable on my floppy drive loose. Kind of strange, but it worked for me.

---

### Post by NaitoNeko on 2005-09-24
[QUOTE=nwjsmith]I have a machine running an AMD Athlon 64 3200+, and my motherboard has an integrated ATI Radeon Xpress x200.

During the Ubuntu amd64 live CD boot, at the ubuntu splash screen, the computer locks up (with no mouse or keyboard functionality).

Also, during the kubuntu amd64 live CD boot, it appears X.org loads fine, but it locks up not much after the background from KDE appears.

Any help would be great.[/QUOTE]
 You need to edit yoy xorg.conf so in the device seccion add.
                      "NoAccel"    "true"
You will notice that your Pc. Could be slow so then install the ati drivers.
I recomment to re-compile your kernel.

---

### Post by mlomker on 2005-09-24
> "NoAccel"    "true"

That probably is the problem.  You could also select 'rescue' from the grub menu and then run **dpkg-reconfigure xserver-xorg** from the command-line.  Select 'vesa' as your video driver and take the defaults for everything else.

Once you get booted you'll want to look into [installing](http://www.ubuntuforums.org/showthread.php?p=348911)  the fglrx video drivers for your card.

---

