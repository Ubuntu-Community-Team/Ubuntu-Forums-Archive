---
title: "kernel help"
date: 2006-06-27
forum: Desktop Environments
---

### Post by twizitid on 2006-06-27
trying to compile a new kernel using the guide that was posted on the forums, everything goes fine until i do :

twiztid@senz:/usr/src/linux$ sudo make-kpkg --initrd --append-to-version=twiztid kernel_image kernel_headers

then i get this error about 30 seconds later:

Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
twiztid@senz:/usr/src/linux$                          


Any ideas on how to fix this? or what it means? This is my first compilation so i'm very unaware as to what to do.

---

### Post by knn on 2006-06-27
[QUOTE=twizitid]trying to compile a new kernel using the guide that was posted on the forums, everything goes fine until i do :

twiztid@senz:/usr/src/linux$ sudo make-kpkg --initrd --append-to-version=twiztid kernel_image kernel_headers

then i get this error about 30 seconds later:

Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
twiztid@senz:/usr/src/linux$                          


Any ideas on how to fix this? or what it means? This is my first compilation so i'm very unaware as to what to do.[/QUOTE]

CONFIG_KALLSYMS_EXTRA_PASS is a setting you can set in xconfig. It's in General Setup/Configure standard kernel features. Try setting it.

But before you do that: Why are you compiling a 2.6.12 kernel? That's a really old version. Ubuntu's kernels are 2.6.15-something and the latest is 2.6.17.1. Those shouldn't have this problem.

---

### Post by twizitid on 2006-06-27
i'll try that...
and i  dont know, i was following a guide in the forums and thats what i downloaded from the rep's. perhaps i should look again.

thanks for the info

---

### Post by knn on 2006-06-28
[QUOTE=twizitid]i'll try that...
and i  dont know, i was following a guide in the forums and thats what i downloaded from the rep's. perhaps i should look again.

thanks for the info[/QUOTE]

You will find the latest kernel and the ck performance patch for it [here]("http://members.optusnet.com.au/ckolivas/kernel/")
Use [this]("http://ubuntuforums.org/showthread.php?t=84174&highlight=kernel+ck") howto (but don't download the kernel and patch linked there, they are a little outdated)

---

