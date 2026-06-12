---
title: "Wubi - can't get past memtest"
date: 2009-02-24
forum: General Help
---

### Post by alecspoons on 2009-02-24
Been using Ubuntu for a while, but new to Wubi.

When I tried to boot my laptop into Ubuntu today, it came up with memtest instead. I let it run (although until today I'd never even heard of memtest) and at the end of the lengthy test, I had the option to reboot. That just brought memtest back up again.

How do I get past memtest? Why can't I just boot into Ubuntu like I did before?

Grateful for any help.

---

### Post by kahlil88 on 2009-02-24
Did you mess with your GRUB configuration recently? It sounds to me like Memtest86+ has somehow become the default boot option. When you turn on the computer, is Ubuntu still a boot option?

---

### Post by alecspoons on 2009-02-24
Thanks for the reply.

Did I mess with the GRUB configuration? Not that I am aware of. I certainly haven't done it deliberately. The only changes I made were when I updated it recently with help from another forum user here: 
[http://ubuntuforums.org/showthread.php?t=1059141](http://ubuntuforums.org/showthread.php?t=1059141)

When I boot up, I can choose Ubuntu, but it just goes straight to memtest and I can't get past that! When it starts to boot, I get the Grub countdown and I can get to the Grub menu where it has Ubuntu and memtest on the same line, but I don't know if that means anything and I don't know what (if anything) I can do there that will help.

Thanks again.

---

### Post by kahlil88 on 2009-02-24
It's kinda misleading how GRUB says "Ubuntu X.XX, Memtest" since it's not actually booting Ubuntu at all. If there are any options that just say "Ubuntu X.XX" choose that, because the Memtest option just tests your RAM and won't actually boot Ubuntu.

---

### Post by alecspoons on 2009-02-24
Thanks again

There are no options that just say Ubuntu. Only 'Ubuntu X.XX, Memtest', like you say.

---

### Post by kahlil88 on 2009-02-24
In that case, you'll probably have to boot from the install disc and try to fix the GRUB config file.

---

### Post by alecspoons on 2009-02-26
Hmnnn...

Thanks again kahlil88.

I reckon that since it's Wubi installation, it might just be easier to uninstall and start again.

---

