---
title: "easy question..."
date: 2005-08-20
forum: Desktop Environments
---

### Post by Joey French on 2005-08-20
When I upgraded (by synaptic) linux-image to amd k7 2.6.11 from the generic 386, I see that I have a few other linux-images installed. Can I simply mark these for comple removal via synaptic? Or am I using the amd k7 kernel, with no need to remove the others?

---

### Post by bored2k on 2005-08-20
[QUOTE=Joey French]When I upgraded (by synaptic) linux-image to amd k7 2.6.11 from the generic 386, I see that I have a few other linux-images installed. Can I simply mark these for comple removal via synaptic? Or am I using the amd k7 kernel, with no need to remove the others?[/QUOTE]
 > Can I simply mark these for comple removal via synaptic? If you installed and are using the k7 kernel, there would be no need to keep the 386 ones. If you mean the K7 restricted modules (etc), you should leave those.

---

### Post by Joey French on 2005-08-20
Okay, well then can you tell me how to check to see which one I am currently using?

Thanks in advance!
Joey

---

### Post by bored2k on 2005-08-20
[QUOTE=Joey French]Okay, well then can you tell me how to check to see which one I am currently using?

Thanks in advance!
Joey[/QUOTE]
 When you started your computer you where asked for the Kernel image you wanted to boot with. If you just installed the k7 kernel, you need to restart and select it. Then you can delete the one you're not using.

---

### Post by cjazz on 2005-08-20
[QUOTE=Joey French]Okay, well then can you tell me how to check to see which one I am currently using?

Thanks in advance!
Joey[/QUOTE]


Open terminal and type:

uname -a

---

### Post by Joey French on 2005-08-21
Thanks. I upgraded my kernel to 2.6.11.1-k7, and it bugs out. Is there any way I can move back to 2.6.10.5-k7, Synaptic says it's mad dangerous?

---

### Post by Joey French on 2005-08-21
bump.

---

### Post by Joey French on 2005-08-21
Okay, I got it covered. Here's what I did, may seem elementary so experts, but some newbies will appreciate. Restarted the system, esc into grub, selected 2.6.10.5 k7 in grub, booted, then removed the new kernel with no problems. Seems simple enough, but not so obvious at the time, mainly because grub didn't show up while booting, like my mandrake install did- every boot. So, anyway, thanks a lot!

---

