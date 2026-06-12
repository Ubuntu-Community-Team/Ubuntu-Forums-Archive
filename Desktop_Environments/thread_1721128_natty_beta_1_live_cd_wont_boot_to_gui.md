---
title: "natty beta 1 live cd wont boot to gui"
date: 2011-04-04
forum: Desktop Environments
---

### Post by reptilezone2002 on 2011-04-04
natty beta 1 live cd wont boot to GUI is hangs & get stuck

---

### Post by galacticaboy on 2011-04-04
> **reptilezone2002 said:**
> natty beta 1 live cd wont boot to GUI is hangs & get stuck

All of the Natty Beta 1's are doing that to me, Ubuntu, Kubuntu, and Xubuntu. None of them will boot GUI, I did get Kubuntu to after about 45 minutes and then the desktop was all buggy and did not load properly. Let me know if you find a solution!

---

### Post by Krytarik on 2011-04-04
Maybe you can boot by passing the ever-popular boot parameters "nomodeset", "acpi=off" or "noapic" to the kernel, add them after "quiet splash":
[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot")

Note: Of course, the boot menu of the installCD looks quite different to those of an installed system, but there is nevertheless the option to pass custom boot parameters.

---

### Post by clhsharky on 2011-04-04
reptilezone2002


Natty has its own sub forum, check it out.
Development & Programming>Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)


Sharky

---

### Post by JeyPeyy on 2011-04-05
I have the same problem. Putting "acpi=off" solves this, but it gives me the classic gnome environment, without hardware acceleration.

Anyone who has found a bug report about this? Or should I submit one?

--posting from the live environment, with classic gnome =(

---

### Post by Krytarik on 2011-04-05
> **JeyPeyy said:**
> I have the same problem. Putting "acpi=off" solves this, but it gives me the classic gnome environment, without hardware acceleration.

I suggest installing it first, and then install the proper video driver that sufficiently supports your video card/chip.

---

### Post by JeyPeyy on 2011-04-05
> **Krytarik said:**
> I suggest installing it first, and then install the proper video driver that sufficiently supports your video card/chip.

Okay, but it isn't very user friendly, so I hope it gets fixed before the release.

---

### Post by Krytarik on 2011-04-05
> **JeyPeyy said:**
> Okay, but it isn't very user friendly, so I hope it gets fixed before the release.
Yeah, you are right! At least the installCD should run without having to tinker with the boot parameters before. But there are always issues with some video cards/chips, also in earlier versions, and it doesn't matter at the end if you run the liveCD or an installed system. This all depends on the kernel and the respective video drivers.

---

