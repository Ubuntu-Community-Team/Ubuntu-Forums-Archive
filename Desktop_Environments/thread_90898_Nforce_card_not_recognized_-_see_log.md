---
title: "Nforce card not recognized - see log"
date: 2005-11-16
forum: Desktop Environments
---

### Post by ThiAm on 2005-11-16
I cannot get Ubuntu to recognize my sound card - Nforce from Nvidia, neither my Nvidia network driver (luckily I have also an USB Belkin adapter which works).

I have first tried to install the Nvidia packages with apt - without success, then I have read some threads about similar issues and been on Nvidia site to download their driver: NFORCE-Linux-x86-1.0-0306-pkg1.run. I follow the install instructions but I get following error message when compiling the Kernel (see log for more details):

-----------------------
ERROR: Unable to load the kernel module 'nvnet.ko'. This is most likely
because the kernel module was built using the wrong kernel source files.
Please make sure you have installed the kernel source files for your
kernel; on Red Hat Linux systems, for example, be sure you have the
'kernel-source' rpm installed. If you know the correct kernel source
files are installed, you may specify the kernel source path with the
'--kernel-source-path' commandline option.
-> Kernel module load error: FATAL: Error inserting nvnet
(/lib/modules/2.6.12-9-386/kernel/drivers/net/nvnet.ko): Invalid module
format
-----------------------

and similar message for the sound driver...

Can anybody help ? Tx.

---

### Post by hw-tph on 2005-11-16
Is there any specific reason you need to use Nvidia's binary driver? The onboard nforce/nforce2/nforce3 network works fine using the forcedeth driver which is in the main kernel tree (and as such included in Ubuntu - it should work right off the bat).

Similarily, the onboard audio should work flawlessly using the snd-intel8x0 driver.

H&#229;kan

---

### Post by ThiAm on 2005-11-16
Sorry for the confusion:
=> My sound card is not detected as device
=> The Ethernet port is found but I have not been able to use it to connect to Internet (via ADSL)

I would be happy to try your suggestion, but how do I check/change default sound or ethernet driver ?

btw I have to use vesa graphic driver i.o. nvidia as described in another Thread because I could not start X windows...  Lot of fun with nvidia apparently...

---

