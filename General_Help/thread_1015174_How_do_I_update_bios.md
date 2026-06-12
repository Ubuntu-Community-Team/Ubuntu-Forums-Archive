---
title: "How do I update bios?"
date: 2008-12-18
forum: General Help
---

### Post by rmhamm on 2008-12-18
I have an asus mva-vm hdmi motherboard and it wasn't exactly meant for linux but that doesn't matter. I need to update the bios to resolve some issues it is having. I've downloaded what asus says is the newest bios/patch/i'm not sure its a .bin file and I have to somehow update the bios without windows, a floppy drive, or pre-existing knowledge of how to update bios.
Could someone give me some advice? I've got a usb and I think I might be able to do it from there as it gives me the option to upload a file in the bios.

---

### Post by taurus on 2008-12-18
You can burn it to a CD and have your BIOS boot from the CD if you don't have a floppy drive.

---

### Post by lykwydchykyn on 2008-12-18
Typically, they will have some kind of DOS-based executable to write that .bin file to the BIOS.  Check with ASUS about that.

If you can get your hands on a bootable DOS disk image, you can use a program like k3b (or whatever GNOME's disc burning utility is, don't know) to create a bootable CD with your .bin file and the updater tool on it.  You might need an actual MS-DOS disk (like a windows 98 boot disk) since I don't think freeDOS has CDRom drivers.

Of course, asus may have a linux-based utility for this, I don't know.  It might be worth checking.

---

### Post by FakeOutdoorsman on 2008-12-18
I've used this with success:

[HOWTO: Flash BIOS, The Ubuntu Way](http://ubuntuforums.org/showthread.php?t=318789)

---

