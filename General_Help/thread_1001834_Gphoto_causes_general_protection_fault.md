---
title: "Gphoto causes general protection fault"
date: 2008-12-04
forum: General Help
---

### Post by nonbiostudent on 2008-12-04
Hi,

I am using a python script to control a Nikon D80 digital camera, taking and processing images about every 30 seconds. The actual communication with the camera is done by making calls to the gphoto2 program using python's Popen command. Unfortunately the system keeps completely freezing up at random intervals - sometimes after a day, sometimes after a few hours. 
I have looked in the kernel log and it is full of general protection faults.

Changing the script to just read test images off of the hard disk (i.e. the same script, except no gphoto calls) fixes the problem entirely and the log no longer contains general protection faults.

I have attached a section of the kernel log containing one of the many GPFs. I was running the Hardy Heron release of Xubuntu (64bit version), although now I have upgraded to Intrepid to see if this makes any difference.

Does anyone have any good tips on figuring this out or what to try next?

Thanks in advance!

---

