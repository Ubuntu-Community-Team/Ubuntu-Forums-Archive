---
title: "Xbox 360 Gamepad issues"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by popiculo on 2008-02-08
I have been following the instructions listed here [https://help.ubuntu.com/community/Xbox360Controller]("https://help.ubuntu.com/community/Xbox360Controller")
.  Everything goes well until I reach the Makefile. I have tried gedit and emacs and I get the same error." Makefile:11: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop" 

I think i understand the error but I dont know how to fix it.  I copy and pasted the commands for the Makefile exaclty like its listed.

```
KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS=-I$(shell pwd)

obj-m:=xpad.o

all:
        $(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install:
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

Any suggestions?

---

### Post by acoustibop on 2008-02-08
From the howto you pointed to, popiculo:
> If the "make" process failed, you are probably missing a file, or the tabs in the Makefile got converted to spaces.

---

