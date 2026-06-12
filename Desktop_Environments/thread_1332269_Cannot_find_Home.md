---
title: "Cannot find Home"
date: 2009-11-20
forum: Desktop Environments
---

### Post by gordon3913 on 2009-11-20
Using Ubuntu 9.10
I have been running Karmic for a couple of weeks without any problems. My home directory is on a seperate partition.
Now I cannot log into Home. A message said that I had to greate a new home directory.
I did this but still could not log into the system.
Problem with the configuration server.
/usr/lib/libgconf2-4/g-conf-sanity-check-2 exited with status 256

How can I get back my home partition?

---

### Post by gordon3913 on 2009-11-20
The message now on the screen says that Nautilus could not create the following required folders:
/home/gordon/Desktop, or set permissions such that Nautilus can create them.

---

### Post by gordon3913 on 2009-11-20
Error- Could not update ICEauthority file /home/gordon/.ICEauthority

I tried the recovery option from the boot menu and used Repair System but it still will not boot into my home partition

---

### Post by gordon3913 on 2009-11-20
All is fixed.
I was having trouble reading my Windows 2nd partition and I must have renamed the partion on the wrong drive. Using mc I was able to change my home back to the correct location.
My system now also reads the Windows D drive which did not happen with the installation of 9.10. This has all of my windows personal files (Windows Home) which I still like to access.

---

