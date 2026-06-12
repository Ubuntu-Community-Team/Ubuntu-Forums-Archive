---
title: "PAE (server kernel) with 4GB RAM not working"
date: 2009-01-08
forum: General Help
---

### Post by Ingenium on 2009-01-08
I have a **Core Duo processor (ie, no 64-bit)** and I recently upgraded from 2GB of RAM to 4GB. I installed the server kernel and booted it, but Ubuntu still only shows 3.2GB of memory. On the generic kernel, dmesg would have an entry saying that PAE isn't enabled and all the memory isn't available; I don't get this message on the server kernel, but it still only sees 3.2GB.

I checked in the BIOS for an option about of memory mapping since I heard this could cause problems, but I didn't see anything. The BIOS shows 4GB of RAM.

The only thing I can think of is that there is some issue with my video card that's causing it. The laptop has Intel integrated graphics, which I believe uses system RAM since it has no dedicated memory itself. Perhaps this is interfering with PAE somehow? 

Any suggestions?

---

### Post by dcstar on 2009-01-08
> **Ingenium said:**
> I have a Core Duo processor (ie, no 64-bit) and I recently upgraded from 2GB of RAM to 4GB. I installed the server kernel and booted it, but Ubuntu still only shows 3.2GB of memory. On the generic kernel, dmesg would have an entry saying that PAE isn't enabled and all the memory isn't available; I don't get this message on the server kernel, but it still only sees 3.2GB.

I checked in the BIOS for an option about of memory mapping since I heard this could cause problems, but I didn't see anything. The BIOS shows 4GB of RAM.

The only thing I can think of is that there is some issue with my video card that's causing it. The laptop has Intel integrated graphics, which I believe uses system RAM since it has no dedicated memory itself. Perhaps this is interfering with PAE somehow? 

Any suggestions?

Go to the 64-bit forum and look at the hundreds of posts covering this subject.

---

### Post by Ingenium on 2009-01-08
> **dcstar said:**
> Go to the 64-bit forum and look at the hundreds of posts covering this subject.

I don't have a 64-bit processor. I've read all the existing threads and they all just say to use a 64-bit kernel, which I obviously can't do.

---

### Post by dcstar on 2009-01-08
> **Ingenium said:**
> I don't have a 64-bit processor. I've read all the existing threads and they all just say to use a 64-bit kernel, which I obviously can't do.

Many of the posts explain what causes this and various ways to get around it, just because you don't have a 64-bit processor does not make the PAE specific ones irrelevant.

You will see most are BIOS issues and have nothing to do with the O/S.

---

### Post by chmac on 2009-01-17
Did you resolve the issues? Was it BIOS related in the end?

---

### Post by Ingenium on 2009-01-17
No I unfortunately didn't resolve the issue. I've looked at every option in the BIOS but nothing affects it. The BIOS itself sees 4GB of memory, and I have the latest BIOS update.

---

### Post by chmac on 2009-01-17
Have you tried searching for your motherboard model and PAE, etc? Motherboard manual? Might other people have the same issue with this board?

It sounds like a frustrating problem, would be driving me nuts! I'm currently debating [PAE versus 64 bit]("http://ubuntuforums.org/showthread.php?t=1042318") if I want to add another 2Gb or 4Gb to my system.

---

### Post by jrusso2 on 2009-01-17
Its normal for a 32 bit OS to only show 3.2 gigs of ram out of four.  Some of it is your video card it can show a bit more.  I am not sure about setting up PAE on Linux but I don't think its even worth it.  If you need to run that much ram run 64 bit.

If you have a core2duo that is 64 bit if its the one before that its 32 bit.

---

### Post by chmac on 2009-01-17
jrusso2, PAE is a valid alternative to a 64 bit kernel as far as I know.

Ingenium, do you see any memory mapping / memory holes / other settings in your BIOS? Have you checked every single screen, googled every last option? I've read that some motherboards simply don't support more than 4Gb, so you may be out of luck. :(

---

