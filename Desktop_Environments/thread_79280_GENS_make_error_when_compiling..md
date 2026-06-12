---
title: "GENS make error when compiling."
date: 2005-10-19
forum: Desktop Environments
---

### Post by abou on 2005-10-19
I donwloaded several versions of GENS and always get the same error after finally installing what seemed to be all the dependencies. When I ./configure everything works fine, but when I &quot;make&quot; I get the following errors at the very end: ```
make[3]: *** [emulator/gens-g_main.o] Error 1 
make[3]: Leaving directory `/home/abou/Desktop/GensForLinux/src/gens' 
make[2]: *** [all-recursive] Error 1 
make[2]: Leaving directory `/home/abou/Desktop/GensForLinux/src' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/home/abou/Desktop/GensForLinux' 
make: *** [all] Error 2
``` This, of course means that I cannot even &quot;make install&quot;. I am new to compiling so as much detail as possible would be great.

---

### Post by amohanty on 2005-10-19
In most cases ./configure will not completely error out even if there is a problem. If you look at the ./configure logs you can tell if something is missing or not. Posting the output of ./configure would be helpful.

AM

---

### Post by abou on 2005-10-19
I attached the configure.log to the post as a text file.

---

### Post by Wolki on 2005-10-20
I remember installing that once... You need to install an assembler (i think it was nasm), configure doesn't notice but make won't work without it.

I'd also suggest installing checkinstall and using "sudo checkinstall" instead of "sudo make install". It will create a .deb and install that, meaning you can uninstall it rather easy. Close synaptic before using it.

---

### Post by abou on 2005-10-21
Still no luck.  I guess I am destined never to compile.:???:

---

