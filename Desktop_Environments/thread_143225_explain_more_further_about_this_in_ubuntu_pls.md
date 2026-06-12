---
title: "explain more further about this in ubuntu pls"
date: 2006-03-12
forum: Desktop Environments
---

### Post by jdash1 on 2006-03-12
hi could anyone help explain me more BRIEFLY about this simple instruction....becoz i can't really understand what should i do with it.im planning to install an appropriate software for my modem but i'm bit confused about this term..could somebody help me about this..pls... Thanks a lot. !
ive already extracted the file in my desktop

this is the third step:

[COLOR="Red"]
3. Review and edit 'Makefile' (if need):

In many cases you will need to correct path to your local kernel

source tree:

KERNEL_DIR=/path/to/linux

Default KERNEL_DIR is '/lib/modules/<kerne-version>/build'. Many Linux

Distributions use directory '/usr/src/linux-<version>' also.

Note: If you are using Linux kernel 2.4, only header files should be

available for build in $(KERNEL_DIR)/include

Another way to pass right value KERNEL_DIR is to use command line

parameter while running 'make':

$ make KERNEL_DIR=/path/to/linux ...



4. Run 'make' command to compile package:

$ make

5. Install. As 'root' user run:

# make install

It will install:

- application 'slmodemd' under '/usr/sbin' directory

- hardware specific drivers (kernel modules) 'slamr' and 'slusb'

under conventional kernel modules directory

- character device nodes '/dev/slamr0-3' with major number 212

(for pci modems) and '/dev/slusb0-3' with major number 213

(for usb modems).

- config modules for autoloading (by editing file '/etc/modules.conf')

(only with 2.4 kernels)[/COLOR]




where is the "**KERNEL**" of which i would place the software ?

**IM USING UBUNTU GNOME BREEZY BADGER 5.10  **
im bit confused about this.....



so when i tried to skip the [COLOR="Red"]THIRD[/COLOR] step i've got some error..


[COLOR="Red"]root@Varias:/home/jdash/Desktop/slmodem-2.9.10# make
make -C modem all
make[1]: Entering directory `/home/jdash/Desktop/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
make[1]: gcc: Command not found
make[1]: *** [modem_main.o] Error 127
make[1]: Leaving directory `/home/jdash/Desktop/slmodem-2.9.10/modem'
make: *** [modem] Error 2[/COLOR]



sorry for being a noob...
pls help...i just placed the installer in my home desktop...am i right just to place it anywhere ?? then execute some commandS ??

---

### Post by GuyveR800 on 2006-03-12
I think you need to 'sudo apt-get install build-essential' and 'sudo apt-get install gcc-3.4' and then repeat step 4.

---

### Post by dcstar on 2006-03-12
[QUOTE=jdash1]hi could anyone help explain me more BRIEFLY about this simple instruction....becoz i can't really understand what should i do with it.im planning to install an appropriate software for my modem but i'm bit confused about this term..could somebody help me about this..pls... Thanks a lot. !
ive already extracted the file in my desktop

this is the third step:

[COLOR="Red"]
3. Review and edit 'Makefile' (if need):

In many cases you will need to correct path to your local kernel

source tree:

KERNEL_DIR=/path/to/linux

Default KERNEL_DIR is '/lib/modules/<kernel-version>/build'. Many Linux

Distributions use directory '/usr/src/linux-<version>' also.

Note: If you are using Linux kernel 2.4, only header files should be

available for build in $(KERNEL_DIR)/include

Another way to pass right value KERNEL_DIR is to use command line

parameter while running 'make':

$ make KERNEL_DIR=/path/to/linux ...
.......[/QUOTE]
In a terminal, do: ```
uname -r
``` the output is what you want to replace the <kernel-version> in '/lib/modules/<kernel-version>/build'

---

