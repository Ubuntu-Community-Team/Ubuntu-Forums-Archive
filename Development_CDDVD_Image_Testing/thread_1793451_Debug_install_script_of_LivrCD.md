---
title: "Debug install script of LivrCD?"
date: 2011-06-29
forum: Development CD/DVD Image Testing
---

### Post by MAFoElffen on 2011-06-29
Okay-- I have some questions...

Background- 
I help support on the "Installation and Upgrades" Support Forum for mainly Graphics Issues.  I have a sticky there for that.  I had 2 users who had "really" basic" skills, similar hardware and were not getting anywhere...

I figured the easiest way to help them was to create a modified LiveCD for them, with the KMS mod's they needed to display correctly...  Uploaded it to one of my shared spaces...  

Note:  I mod'ed the boot options of "Try" and "Install" // not anything in the install process...

One user... resolved, installed and taken care of... The other, can now run the Live Image perfectly, but when he goes to install, it hangs somewhere in the process.  This user also has another box that he used this mod'ed LiveCD on and it installed fine from...

So I guess the question is- Is there an install log created in that process, that I can look through to debug and see where it is hanging? A filename and location I can tell this user to copy and post?

---

### Post by MAFoElffen on 2011-06-29
If not it's own install / progress log, I'm thinking I could go through the /var/log/syslog and /var/log/dmesg... but just was wondering if there was something "easier" and more direct.

I guess I could load this iso in virtual and see what changes in the install process and what it is doing when it gets to the screen that user says it locks up in...

---

