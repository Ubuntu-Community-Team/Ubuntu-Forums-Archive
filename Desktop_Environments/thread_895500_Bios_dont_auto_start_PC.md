---
title: "Bios dont auto start PC"
date: 2008-08-20
forum: Desktop Environments
---

### Post by dbruynb on 2008-08-20
Hi, I am busy moving from windows to Kubuntu and currently dual boot. 
The problem is when I shutdown the pc from Kubuntu it won’t auto start at the time that is set in the BIOS but when I shutdown from windows it does startup. I understand that when the OS shutdown it should set a bit in the BIOS that the pc is off and Kubuntu does not set the bit and the BIOS does not start the pc because the BIOS thinks the pc is on while in actual fact the pc is off.

So, how do I make Kubuntu set that bit so that my pc can auto start at the time it was set?

---

### Post by carolinason on 2008-08-22
Just an idea - it could be an apm or acpi issue. start-up scripts are in /etc/rc2.d and look in your bios to see which one you use.

---

