---
title: "Boot Problem"
date: 2006-09-13
forum: Desktop Environments
---

### Post by bobap1950 on 2006-09-13
I had a problem re-installing Ubuntu after upgrading my system.  I added a new Foxconn MB with two WD SATA drives and AMD X2 CPU.  I have a dual boot system with XP on one drive and Ubuntu on the other.  I found that if I disabled the APIC in the BIOS I could install Ubuntu.  Now I can't log into Windows XP unless I enable APIC and then I can't log into Ubuntu unless I disable it again.  I don't want to have to go into the BIOS and make changes every time.  I would appreciate any information you have as how to correct this problem

Thank you for your time and help.

Bob  8-)

---

### Post by tuxinvader on 2006-09-13
Did you try editing your grub config and adding the "noapic" option to your boot line in grub? 

edit /boot/grub/menu.lst

append "noapic" to the line begining "# kopt="

Don't remove the "#"

[EDIT] -- run "sudo update-grub" after

---

