---
title: "Stop Udating 386 Kernel"
date: 2006-07-17
forum: Desktop Environments
---

### Post by El Guapo on 2006-07-17
I have a question.  I updated my system to use the 686 optimized kernel.  However my system continues to tell me that there are updates for the 386 kernel.  I don't wan't to use that kernel, therefore there is no need to update it.

How do I adjust things so that it does not continue to try to update a kernel that I never use?

---

### Post by ohgod on 2006-07-17
Fire up synaptic and search for 'linux-image'.  Unmark the package called 'linux-image-386' and that should do the trick.

---

### Post by asplode on 2006-07-17
you might have to go through all the linux- packages in synaptic and remove all with references to 386, such as the linux-restricted-modules-386, linux-headers-386, and other various subpackages of the linux kernel that are marked with 386.

---

### Post by az on 2006-07-17
> **ohgod said:**
> Fire up synaptic and search for 'linux-image'.  Unmark the package called 'linux-image-386' and that should do the trick.

Remove all of the 386 linux packages.

---

### Post by El Guapo on 2006-07-18
I think removing them sounds like the best and easiest idea yet.  Why didn't I think of that in the first place? :-k 

Thanks.

---

### Post by sread on 2006-07-20
Hello forum! I also just updated my kernel to 686. I wasn't sure if I would see an improvement, but GNOME loaded almost twice as fast on login! However, my update manager would still like me to update to the latest 386 kernel. I'd rather not remove the 386 kernel incase something goes wrong (as suggested in the excellent kernel update thread). Does anyone know of another way to stop the update manager from trying to update the kernel? I'm sure it means well, but I'm really happy with the 686 kernel :)

-Stuart

---

### Post by 5-HT on 2006-07-20
> **sread said:**
> Hello forum! I also just updated my kernel to 686. I wasn't sure if I would see an improvement, but GNOME loaded almost twice as fast on login! However, my update manager would still like me to update to the latest 386 kernel. I'd rather not remove the 386 kernel incase something goes wrong (as suggested in the excellent kernel update thread). Does anyone know of another way to stop the update manager from trying to update the kernel? I'm sure it means well, but I'm really happy with the 686 kernel :)

-Stuart

You could remove linux-386 as that package is simply a metapackage that depends on the most recent 386 kernel and restricted modules.

NOTE: If you remove linux-386 using Aptitude, depending on your Aptitude config, you may need to mark all the 386 kernels and restricted modules you would like to keep as 'manually installed'. You will not have to do anything special if removing the package via apt/synaptic.

---

### Post by az on 2006-07-20
> **sread said:**
> I'd rather not remove the 386 kernel incase something goes wrong 

-Stuart

Rubbish.

You should not delete your old kernel before booting into the new one.  Other than that, remove them.  Otherwise, it's exactly like saying you are going to keep two copies of firefox on your system in case something goes wrong!

---

### Post by sread on 2006-07-21
Thanks folks.
-Stuart

---

### Post by Scythe!? on 2006-08-03
I'm trying to do this too, but I can't unmark linux-386, its blacked out. Any ideas?

---

