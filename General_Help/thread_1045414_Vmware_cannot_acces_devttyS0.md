---
title: "Vmware cannot acces /dev/ttyS0"
date: 2009-01-20
forum: General Help
---

### Post by svennils on 2009-01-20
Hi, i've just reinstalled vmware after deleting off  my last windows partition on my laptop. I got everything up and running, but when i start the guest OS, vmware complains that "
"serial0: The "/dev/ttyS0" file does not appear to be a serial port: Input/output error.
Failed to connect virtual device serial0.""

I've googled this, and searched the forums, tried chmod 666 on the tty, no change. 
Minicom has the same issue, unless i run it as root. Running vmware as root (with gksudo) gives me a black screen in the guest OS, it somehow does not get the right screen res. from the x server, so it is not an option. How do i get get ttyS0 access? I need it for a programming cable, and it has been working before (some years since i used it).
Hoping for some help, 
Sven.

---

### Post by dcstar on 2009-01-20
> **svennils said:**
> Hi, i've just reinstalled vmware after deleting off  my last windows partition on my laptop. I got everything up and running, but when i start the guest OS, vmware complains that "
"serial0: The "/dev/ttyS0" file does not appear to be a serial port: Input/output error.
Failed to connect virtual device serial0.""

I've googled this, and searched the forums, tried chmod 666 on the tty, no change. 
Minicom has the same issue, unless i run it as root. Running vmware as root (with gksudo) gives me a black screen in the guest OS, it somehow does not get the right screen res. from the x server, so it is not an option. How do i get get ttyS0 access? I need it for a programming cable, and it has been working before (some years since i used it).
Hoping for some help, 
Sven.

The settings for VMWare serial ports in VMs are up to you, check the setting.

Also, ask VM questions in the Virtualization forum.

---

### Post by svennils on 2009-01-20
i have already tried the serial port settings, since i had to create the port link. Like said, the problem is not a missing port, but the fact that some processes  with user privileges cannot acces /dev/ttyS0, despite my user account being in the dialout group, and the ttyS0 having root:dialout permission. Minicom has the exact same problem unless i run it as root.I will post this in the virtualization forums instead, could a admin please close this thread?

---

