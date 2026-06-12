---
title: "Interact with an &quot;embedded&quot; terminal"
date: 2008-12-10
forum: General Help
---

### Post by blazemore on 2008-12-10
Some applications (for example Synaptic) have a built in terminal to display details.
An application called KernelCheck has finished downloading and compiling a kernel (!) but now it's asking me a simple question about GRUB. I can't interact with it at all!
Is there a way I can sort this?

---

### Post by adult swim on 2008-12-10
have you tried hitting the tab key and then using the arrow keys?

---

### Post by blazemore on 2008-12-10
Would I be posting here if I had?

---

### Post by adult swim on 2008-12-10
ive seen people try to click.  is the process still running?  if its stuck you may just have to kill the process, which might kill dpkg so youd have to configure it and then edit your grub menu manually to reflect the new kernel.

---

### Post by blazemore on 2008-12-10
That's what my friend said. What would I put in? Should I do update-grub?

---

### Post by adult swim on 2008-12-10
you could try that and see if it recognizes the new kernel.  if it doesnt and the kernel is on the same partition as the other ones already in your menu.lst you could just copy a section and then paste it in, but change everywhere that says  kernel 2.6.28-2-generic (or whatever you have) with the new kernel name.

---

### Post by blazemore on 2008-12-10
I rebooted, and did update-grub and most importantly dpkg --configure -a, which fixed it. I now boot in 18 seconds (according to bootchart)

---

