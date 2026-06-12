---
title: "HELP on Dell Dimension 2400!!!"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by squeabs on 2009-06-12
I'm trying to boot up an Ubuntu CD on a Dell Dimension 2400, Pentium 4. It's got two disc drives. One is a CD-RW, the other is a DVD. I'm guessing that the one I want to boot from is DVD.

I insert the Live CD, try to boot from CD (actually gives me a strange name: IDM CD Device). It fails, even after trying 8.04, 8.10, and Xubuntu 8.04. These are Ubuntu CDs that are known to work on any other computer I've tried booting them on.

I need to use the Live CD features to wipe a computer for my girlfriend's parents. Then I'll be re-installing Windows. It's what they want, but I want to use the Live CD to effectively destroy the information on the hard disk.

If anyone knows of a better way to do this, please let me know. I've got two weeks to complete this.

---

### Post by coffeeaddict22 on 2009-06-13
Hi,
Sounds like a BIOS setting.  What happens?  Does it try to boot from the CD at all?  If not, go into the BIOS and find the option that allows you to boot from a CD _before_ the hard drive.

---

### Post by squeabs on 2009-06-13
The first time, I manually tried to boot from CD. It tried, but failed. Then I set the CD drive to boot first and it still failed. Is Windows somehow messing up the BIOS? This computer is pretty bogged down - probable viruses, spyware, etc. - and runs very slow. If Windows is messing it up, how would I be able to fix it?
The only solution I came up with is to re-install Windows via the system re-install disk that came with the computer, then try booting from ubuntu to effectively wipe the drive. I don't know if it'll work, though.

---

### Post by coffeeaddict22 on 2009-06-14
If you can't boot from the Ubuntu CD, you shouldn't be able to boot from the Windows CD.  Does the CD player work?

---

### Post by squeabs on 2009-06-14
I'm about to test that today. I'll post back with the results.

---

### Post by Therion on 2009-06-14
> **squeabs said:**
> I'm trying to boot up an Ubuntu CD on a Dell Dimension 2400, Pentium 4. It's got two disc drives. One is a CD-RW, the other is a DVD. I'm guessing that the one I want to boot from is DVD.
No, most likely the CD drive is the bootable device, not the DVD drive.  

Try a bootable CD in the CD *drive*.

---

### Post by squeabs on 2009-06-14
I had tried that, but I've figured it out! For anyone else having this problem, here's how I fixed it.

In the System Settings at boot, go into Drive Configuration. There are options for Primary Slave and Secondary Slave. The DVD drive was set as the Primary, so every time I tried to boot from CD, it looked in the DVD drive. I disabled the Primary Slave drive, so the computer had no choice but to boot from the Secondary Slave, which is the CD-RW drive I was trying to boot from in the first place, or should have been trying to boot from instead of the DVD.

The computer does boot from CD. I used Wubi to set it up so that I could boot from the Live CD. Once in there, I deleted the entire hard drive. Afterwards, I had to go into the System Settings as described above to boot from the Dell Recovery Disks.

Thanks for the help and I hope this helps anyone else having the same problem.

---

### Post by synchro505 on 2009-06-15
It's too bad that you only were using the Live CD as a way to wipe the drive in lieu of installing Windows. 

If your girlfriend's parents only knew how well Ubuntu works (as with many modern Linux builds these days), perhaps they would reconsider. Unless they absolutely need a specific Windows application(s) or something, I would see no need to make them suffer like that!

Anyway, I'm glad that you figured it out. Cheers!

---

### Post by squeabs on 2009-06-15
Unfortunately, they don't even know what linux is. However, I've taken precautions so that I will hopefully never have to do this again. I set them up with a standard account and warned them not to touch the admin account unless absolutely necessary. I don't know why windows doesn't lock specific features like linux and macs do.

---

