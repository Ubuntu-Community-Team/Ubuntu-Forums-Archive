---
title: "Old laptop powers off during boot!"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by ztiruam on 2007-09-01
I have tried to install Ubuntu, Kubuntu and XUbuntu on my old Dell L400.

All with the same problem: During boot it powers off, or hibernates rather.

If I choose recovery mode, and then startx things work - but even after updating the system the boot-problem is still there.

What to do?

---

### Post by Arch2 on 2007-09-01
I assume you're trying to install 7.04 Feisty Fawn. I don't think this problem occurs with 6.06 Dapper Drake. 
When the main screen shows up from the install CD press F6 for other options. A line shows up that says Boot options.... 
Add acpi=off to the end of that line then press enter. 

This will keep the L400 from going into sleep mode. Also the cooling fan works properly with acpi off.

After ubuntu is installed you'll want to make sure acpi=off is at the end of the line that starts with kernel in the /boot/grub/menu.lst file.

---

### Post by ztiruam on 2007-09-02
Problem solved! Thank you!

---

