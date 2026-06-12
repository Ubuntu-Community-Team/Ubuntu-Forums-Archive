---
title: "Removing new kernel?"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Bjamin0325 on 2005-12-27
Hi, everybody.  After a lot of work, I got a good install of Breezy, but as usual, I updated the kernel when prompted, and now my machine rarely boots up unless I watch it for freezes and ctrl+c at startup.

I've changed the grub file to boot the old kernel, but the same thing happens at startup.  Should I remove the new kernel?  Do I do a 'complete removal'? I've searched the forum for anything like this and couldn't find a solution, so sorry if this has been posted a lot. 

Does anyone have any advice?

Thank you all.

Ben

---

### Post by Bjamin0325 on 2005-12-27
bu mp

---

### Post by Dr. Nick on 2005-12-27
If you can select your old kernel from the grub menu and your system runs fine than you can use synaptic to remove the new (buggy) kernel. You can just remove it or do a complete removal it really doesnt matter. A complete removal should take any custom configuration with it but either way you shouldnt have it anymore if you remove it.

If booting into your old kernel causes problems now when it didnt before it may not be a kernel problem but instead another package. Are you sure the kernel was the ONLY update, or were their other updates that you installed that could have causes this behavoir?

---

