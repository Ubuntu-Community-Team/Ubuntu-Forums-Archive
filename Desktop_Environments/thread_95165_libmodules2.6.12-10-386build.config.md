---
title: "/lib/modules/2.6.12-10-386/build/.config"
date: 2005-11-25
forum: Desktop Environments
---

### Post by Termina on 2005-11-25
Since I'm unable to remove this thread, nor edit the subject, I'll just ask my new question here.

When compiling rtl8180 ([http://sourceforge.net/projects/rtl8180-sa2400/)](http://sourceforge.net/projects/rtl8180-sa2400/)), I get this error. Any help?

/home/will/Desktop/rtl8180-0.20.2/r8180_core.c: In function &#8216;rtl8180_pci_probe&#8217;:/home/will/Desktop/rtl8180-0.20.2/r8180_core.c:3263: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
make[2]: *** [/home/will/Desktop/rtl8180-0.20.2/r8180_core.o] Error 1
make[1]: *** [_module_/home/will/Desktop/rtl8180-0.20.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [2.6] Error 2

---

### Post by irishpunk on 2006-02-21
I'm having this same problem.  Any answers on it?

---

### Post by hajk on 2006-02-21
Make sure that you compile with gcc-3.4 by using the command 
"export CC=gcc-3.4". Then "make clean" before you try to compile again.

---

### Post by Vulkano on 2006-03-05
I have another error with this same driver. In this case it says after command "make"

Makefile:8: /lib/modules/2.6.12-9-386/build/.config: No such file or directory
make: *** No rule to make target `/lib/modules/2.6.12-9-386/build/.config'.  Stop.

in fact, the /lib/modules/2.6.12-9-386/build/.config does not exist. Moreover, the /build directory does not exist in my file system.

I'm using kubuntu Breazy 10, and have a 2.6.12 kernel (as far as I know cause I don't know much about Linux yet but am trying to learn fast). My box is a DELL Latitude C-600 laptop.

I tried what you said (export CC=gcc-3.4) and nothing happened, the same error keeps coming up.

I've tried another option, which appears in the following thread:

[http://ubuntuforums.org/showthread.php?t=95879&highlight=rtl8180](http://ubuntuforums.org/showthread.php?t=95879&highlight=rtl8180)

As it says, I downloaded the file and untarred the debian package for this chipset and then "just installed by  sudo dpkg -i file_name.deb" as it said in the post. But for me it was not "just install...". So far, I have not been able to get the card even up!

Thanks in advance for the help

---

