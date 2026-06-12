---
title: "DIfference between Mounting and Enabling Read/Write support?"
date: 2009-03-20
forum: General Help
---

### Post by mahela007 on 2009-03-20
I have dual booted windows with Kubuntu. However I want to automatically mount the windows partitions at start-up. While I was looking at scripts which could help me with this I came found two phrases called "mounting" and "enabling read/write" for a partition. What's the difference between the two?

---

### Post by 505 on 2009-03-20
Mounting is making any partition (part of a hird drive) available to your system.

Windows partitions are stored in NTFS. Some time ago Linux could only read from such partitions, read/write was experimental. In might still be. Therefore, when talking about NTFS, you still see things about read/write support. When talking about mounting NTFS, it means read-only, in this context.

---

