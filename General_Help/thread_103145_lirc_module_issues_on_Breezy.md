---
title: "lirc module issues on Breezy"
date: 2005-12-13
forum: General Help
---

### Post by lehel.kulcsar on 2005-12-13
Hello everyone !

I have googled on this for some time now and i did not find a solution. 
I have installed the kernel image and the lirc packages from the repositories, I have configured the lirc related files for my homebrew IR receiver for serial port 1 and irq =4. 
I also instaled the kernel package for the make-kpkg tool.

According to the readme of the lirc modules the following command must be run:

lehel@rohan:/usr/src/linux$sudo make-kpkg --revision 2.6.12 modules-image

and this is a part of the output:
.....................
make[7]: *** [/usr/src/modules/lirc/drivers/lirc_serial/lirc_serial.o] Error 1
make[6]: *** [_module_/usr/src/modules/lirc/drivers/lirc_serial] Error 2
make[6]: Leaving directory `/usr/src/linux-source-2.6.12'
make[5]: *** [lirc_serial.o] Error 2
make[5]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_serial'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_serial'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: *** [serial] Error 2
make[2]: Leaving directory `/usr/src/modules/lirc'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/lirc'
Module /usr/src/modules/lirc failed.
Hit return to Continue

Do any one have any suggestions ?
Do someone managed to install the lirc on breezy ?

Thanks in advance !

:confused:

---

### Post by toganet on 2006-05-21
I'm having a similar problem, only with the lirc_gpio module.  It's really cramping my style on me mythtv box, and was working on this machine before a reinstall.  I'm currently at a loss.

---

