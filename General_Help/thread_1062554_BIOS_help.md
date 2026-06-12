---
title: "BIOS help"
date: 2009-02-07
forum: General Help
---

### Post by a_toff on 2009-02-07
I'm trying to get xubuntu set up on an old computer at the school where I teach... we don't have many resources and I'm trying to make the best of some disused equipment.

The machine-in-question is a Pentium-something ASUS with an installation of XP, wich I don't have user-password info for. Also the BIOS was/is password protected, so I couldn't use the Live CD to install.

I followed some advice and opened up the machine and removed the battery from the motherboard with the aim of resetting the BIOS options. I left the battery out for about 30 minutes, and then put everything back together.

Now, however, when I power-up the machine, nothing happens. No startup whatsoever. The hard-drive spins up, the fan comes on, it spins the CD drive, and then nothing.

Is there anything I can do to get this machine operational?

---

### Post by mb_webguy on 2009-02-07
Make sure the CMOS battery is seated properly, and that all cables are well-connected.  Most of the time problems like this are caused by cables accidentally pulled loose while you were rummaging around inside the computer.  If you're absolutely sure everything's connected as it should be, then you may have some faulty hardware.

Once you do manage to power up the computer, you should see the standard POST screen.  You'll need to immediately go into the BIOS setup utility (F8? F5?  I never can remember...) and configure the BIOS.  If there's a "default configuration" option, that's a pretty good place to start.

---

### Post by Taras.M.K on 2009-02-07
and be sure your battery's still alive, may be you need to take a new one

---

### Post by a_toff on 2009-02-07
I figured it out... should've known it would be something so simple:

Once the BIOS settings were wiped the system was waiting for the BIOS-setup key to be pressed. After hitting the delete key the setup utility loaded as expected.

Now, however, the mouse and keyboard (not USB but PCI), are not being recognized... Both were working fine before I wiped the BIOS settings.

Perhaps I need to set up the BIOS to recognize PCI at startup?

Luckily I have temporary access to a USB keyboard, which seems to be recognized properly at start time.

---

### Post by Taras.M.K on 2009-02-08
I was sure BIOS had had to set default settings. Anyway it works now :)
I think you mean PS/2 keyboard and mouse. Well, you need now to check all settings in BIOS. But do not try to change anything quickly if you aren't sure. Often, there is an option something like "load optimal performance settings" in BIOS, you may try it.

---

