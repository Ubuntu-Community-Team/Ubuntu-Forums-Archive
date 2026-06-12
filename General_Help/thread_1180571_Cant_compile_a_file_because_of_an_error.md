---
title: "Cant compile a file because of an error"
date: 2009-06-07
forum: General Help
---

### Post by X1R1 on 2009-06-07
K so I followed the instructions to install my xplorer drivers ([https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller))

and whenever I type "make" on a terminal this happens:

```
x1r1@DESKTOP:~/xpad$ make
make: *** No hay ninguna regla para construir el objetivo `make', necesario para `all'.  Alto.
```

on english that would be: there is no rule to build the objective "make", needed for "all". Halt

here is my makefile

```
KERNEL_PATH ?= /usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS =- I$(shell pwd)

obj-m :=xpad.o

all :$(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install :cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

is there a syntax error somewhere or something? please help out i suck at compiling lol to many little details. what am I missing in order to make this error dissapear?

regards and thanks for the help!

---

### Post by mc4man on 2009-06-07
does your actual makefile look like what you posted or what's below?, only asking because a 'code' box should keep the formatting.
 
from link
> Make sure the tabs under "all:" and "install:" remain intact. 
```
KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS=-I$(shell pwd)

obj-m:=xpad.o

all:
        $(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install:
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

in other words you should copy and paste from the how to to your makefile, don't change the formatting, spacing. There is a difference between using the space bar and a tab inset

If typing,  for example

all:[COLOR="Blue"]<press enter>[/COLOR]
[COLOR="Blue"]<press tab>[/COLOR]$(MAKE) ect...

---

### Post by X1R1 on 2009-06-07
My makefile looks like what I put on the "code" box. gonna try your tips and then come back again to tell you if it worked :D

got it!!!! reason was because when I pasted it the TAB got replaced with spaces. Thank you!

---

