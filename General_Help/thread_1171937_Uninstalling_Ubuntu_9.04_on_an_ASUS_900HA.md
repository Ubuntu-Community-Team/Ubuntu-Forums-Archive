---
title: "Uninstalling Ubuntu 9.04 on an ASUS 900HA"
date: 2009-05-27
forum: General Help
---

### Post by Epidemic_HardyBoy on 2009-05-27
Hello, I am asking if anyone here can tell me how to "Uninstall" my Ubuntu. I am dual-booting with windows XP on my eeepc from ASUS.

Specs:
Manufacturer | Asus
Model name | Eee PC 900HA
CPU type | Intel Atom (Diamondville)
CPU speed | 1600 Mhz
Graphics | Intel GMA 950
OS | Windows XP Home
Display | Size 8.9" 1024 X 600
RAM | 1024 MB
Hard Disk | 160 GB
Keyboard | YES
Mouse Pointer | YES

I am uninstalling Ubuntu because of two reasons.

1) The GRUB bootloader is a pain since I have to pick XP most of the time
2) I virtually NEVER use ubuntu.

Can anyone please help me?

---

### Post by Sheffy on 2009-05-27
go into windows

google "free partition editor"

click on the first one (i think)

download it

delete the ubuntu partition 

resize windows and youre done

---

### Post by Epidemic_HardyBoy on 2009-05-27
That wont work, due to the GRUB "overwriting" the Windows MBR (Windows BOOTLOADER) it would make my computer not start at all.

---

### Post by bboston7 on 2009-05-27
> **Epidemic_HardyBoy said:**
> That wont work, due to the GRUB "overwriting" the Windows MBR (Windows BOOTLOADER) it would make my computer not start at all.

You have to restore the MBR after you delete your ubuntu partition.  

1.  Boot from Windows XP disk
2.  Press R to start the restoration console. 
3.  Type FIXMBR
4.  Hit Y

Seriously, why didn't you just google it?  I don't even run xp...

---

