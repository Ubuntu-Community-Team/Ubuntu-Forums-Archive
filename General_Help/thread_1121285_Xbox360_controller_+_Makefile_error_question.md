---
title: "Xbox360 controller + Makefile error question"
date: 2009-04-09
forum: General Help
---

### Post by thelastunavail on 2009-04-09
Hello, I recently read the tutorial [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) to use my xbox 360 controller to play games in ubuntu (esp. snes emulator)

and i got to the create a Makefile part and when I typed the first command "make" it gives me this error "make: *** No rule to make target `make', needed by `all'.  Stop." 

this is my Makefile, it is named "Makefile" as advised by the tut and contains the code

```
KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS=-I$(shell pwd)

obj-m:=xpad.o

all:$(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install:cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

I am useing Ubuntu hardy heron, the xpad directory contains a Makefile, xpad.c and xpad.h files..

am I suppose to change something in that code to match with my configuration or something? Any help is apprciaited, i am new to Linux, thanks!

---

### Post by thelastunavail on 2009-04-09
Help .. plz?? thats the only gamepad i have for a pc and really want to play some old school snes games

---

### Post by pbotros1234 on 2009-04-09
From the article you linked in your post:

> ...In your working directory ("xpad"), copy and paste the following to a file called "Makefile", using your favourite editor. **Make sure the tabs under "all:" and "install:" remain intact.**

As it says, make sure the tabs under "all" and "install" remain intact :)

---

### Post by thelastunavail on 2009-04-09
> **pbotros1234 said:**
> From the article you linked in your post:



As it says, make sure the tabs under "all" and "install" remain intact :)

I apologize, but I dont know what that means to keep "the tabs intact" I copy and pasted it exactly how it was from that thread to gedit and it did not work still. It said there were 8 spaces instead of a tab or something for the error.. :( so i deleted all the spaces between all and install and added a tab and got a new error..

I am new to "Makefile", thanks for all help

---

### Post by thelastunavail on 2009-04-09
What do you mean by keeping them intact? please, I beg of you! hehe

It sucks playing super mario on my keyboard. I just copy and pasted it to gedit then saved it as "Makefile" and got the error.. so it should be intact if i copy and pasted it directly how it is from the thread right?

Or do I have to change some variables in the Makefile somewhere?
thanks

---

### Post by soltanis on 2009-04-10
Try changing to this

```

KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS=-I$(shell pwd)

obj-m:=xpad.o

all:
_make modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install:
_cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```

See where I put the underscores? Make them tabs.

---

### Post by thelastunavail on 2009-04-10
Soltanis:

Thanks man worked like a charm, I was putting a tab directly after the all:instead of hitting enter so it goes to the next line directly after all: and then tab..

So now my /xpad directory contains the files..
Makefile   Module.symvers  xpad.h   xpad.mod.c  xpad.o
Makefile~  xpad.c          xpad.ko  xpad.mod.o

I did everything as it is explained, but when I goto joystick calibrator it wont calibrate the stick or find it automatically, i have to manually type xpad in the top bar, and when i hit calibrate the circle does not move when i move the controllers. I also noticed this erro during calibration in the terminal "Failed to set joystick xpad correction values: Inappropriate ioctl for device"

any ideas? This is the first time i have ever set up a game pad on linux/ubuntu - and dont see a place in the options for a gamepad config besides the jcalibrate app i installed from the tut, I think i'm almost there! :-) thanks!

---

### Post by thelastunavail on 2009-04-10
I did everything correctly by the tutorial and still not working, then I remembered that my xbox 360 wired usb controller is not an official MS 360 controller it is a generic made by pelican.. could this be the reason why it is not working?

---

### Post by thelastunavail on 2009-04-10
Someone ^up there has to know.. can i get some help on this plz, i promise to help others with this same question once i figure it out.. ):P

---

### Post by thelastunavail on 2009-04-10
> **thelastunavail said:**
> Someone ^up there has to know.. can i get some help on this plz, i promise to help others with this same question once i figure it out.. ):P


just seen someone had a simular question as this.. plz help^^ ](*,)

---

