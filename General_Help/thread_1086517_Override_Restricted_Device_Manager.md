---
title: "Override Restricted Device Manager"
date: 2009-03-04
forum: General Help
---

### Post by Halfdood on 2009-03-04
Hi everyone.

I am currently working an application that makes use of the Digital Persona fingerprint scanners.

I finally managed to compile and install the drivers for Ubuntu 8.04 and the sample applications worked fine.

The next time I booted my pc the restricted driver manager had picked up the driver and promptly disabled it. What I mean by disable is that the Enabled checkbox is marked, but the status is not in use. Unchecking, rechecking and restarting does not solve the problem.

Is there a way to circumvent the restricted driver manager? is there a config file somwhere that i must edit that I do not know about (very likely as I have only used linux for about a week now)?

As i have said, the driver worked fine when it was loaded. I can find the ko file under driver/biometrics when i run modprobe -l so I am confident that the driver is installed. It seems to me that the manager disabled it for some reason.

Any help would be greatly appreciated. No advice is too trivial.

Thanx a lot

---

