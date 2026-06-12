---
title: "Long time to sign-in with 10.04"
date: 2010-09-19
forum: Desktop Environments
---

### Post by sandman3838 on 2010-09-19
Hello

With Ubuntu 10.10 just around the corner, I'm probably wasting time writing  this.  I suspect that this issue is addressed on the new release.   I hope so!  Still I had to ask just in case?

It all has to do with my boot-up speed, both with or without user sign-in. 

If I have the system set to boot up straight onto the desktop, its fast.  Great no problem!

However, If I activate user sign-in, it takes a good 1.5 min to 2 min for the sign-in screen to show?  Now I am the only user.  But for security reasons I like having user sign-in activated.  I should also mention that originally right after I did a fresh install of Ubuntu the sign-in timing was not an issue.  Also I am using a NVIDA 9800gt card, and I remember reading that there was some issues with NVIDIA and Plymouth.  If it's related to this I don't know?

Has anyone out there come across and information as to the why and is there a fix?

---

### Post by mathgeek2000 on 2010-09-19
I've read a lot about how they improved boot up time for 10.04, my current release. -- I have an encrypted home folder and must use my logon password.

However: and it may all be in my head, since the newest Kernel : 2.6.32.24.25-generic, there seems to be a longer delay between pressing enter to load the kernel at the Grub menu screen, and the start of text, as the kernel & initial Ram drive are executing. --- I took out the 'quiet splash' entries.

---

