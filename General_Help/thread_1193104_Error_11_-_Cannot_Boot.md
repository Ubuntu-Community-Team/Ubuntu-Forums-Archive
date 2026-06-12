---
title: "Error 11 - Cannot Boot"
date: 2009-06-21
forum: General Help
---

### Post by gruntlips_ on 2009-06-21
I just installed some updates from update manager and after being asked for a restart I can no longer boot.  I get - error 11, Unrecognized Device String, press any key to continue.  I have tried all the boot options and no luck.

I have a serval system 76, amd64, 9.04, and I am not dual booting.

How do I fix this?  Help!

- Chris

---

### Post by Legace on 2009-06-21
Try this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB)

---

### Post by gruntlips_ on 2009-06-21
Thanks Legace, but I didn't install windows and this document does not mention my issue directly or how to fix it.  

Does anyone have an clear list of instructions on how to fix this problem or what even happened in the first place?

- Chris

---

### Post by Legace on 2009-06-21
> **gruntlips_ said:**
> Thanks Legace, but I didn't install windows and this document does not mention my issue directly or how to fix it.  

Does anyone have an clear list of instructions on how to fix this problem or what even happened in the first place?

- Chris

Yes, but this will probably fix the issue even though you haven't installed Windows. You should give it a try..

---

### Post by gruntlips_ on 2009-06-21
I see what you mean.  I have never messed around with my bootloader and don't want to hose my system further.  Which steps do you think I should try? The first part where I would overwrite my windows bootloader using a live ubuntu disk? Or using the supergrub disk?

---

### Post by Legace on 2009-06-21
Use the "Quick Start" method:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start)

So yes, the first part where you will replace the Windows bootloader.

---

### Post by gruntlips_ on 2009-06-21
How do I boot from the live cd to fix this (as in the first step of the instructions)?  I assume if I want to fix the bootloader and not erase my system I select the option "rescue broken computer"?

Thanks,

- Chris

---

