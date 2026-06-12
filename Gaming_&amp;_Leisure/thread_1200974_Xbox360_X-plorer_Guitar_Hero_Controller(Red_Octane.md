---
title: "Xbox360 X-plorer Guitar Hero Controller(Red Octane)"
date: 2009-06-30
forum: Gaming &amp; Leisure
---

### Post by guitar_man on 2009-06-30
I've just used Xbox360 X-plorer Guitar Hero Controller(Red Octane) on frets on fire and I thought that I needed to install driver for my controller.

When I plug the controller on my computer,the led indicator works.
And I tried it on frets on fire and configure the keys(thats all I did)
and it just simply work.Works even better then on windows(you need to install driver for their own product)

I was really planning to play with this controller,thinking that I need to run commands in the but there it goes it just simply work.AMAZING:guitar::guitar:


I'm posting this for those who are planning to use this same exact controller on Ubuntu cause I spend a lot of time searching the net for fixes and other alternative for FOF..and this controller just work,,:guitar:

---

### Post by Erik765 on 2009-07-01
I plug in my controller, but it doesn't work. FoF, doesn't recognize anything from either of my joysticks when trying to configure keymapping...

I tried the directions from [https://help.ubuntu.com/community/Xbox360Controller]("https://help.ubuntu.com/community/Xbox360Controller")

and when I run make it returns:

> erik@erik-desktop:~/.xpad$ make
make modules -C /usr/src/linux-headers-2.6.27-11-generic SUBDIRS=/home/erik/.xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/erik/.xpad/xpad.o
/home/erik/.xpad/xpad.c: In function &#8216;xpad_open&#8217;:
/home/erik/.xpad/xpad.c:382: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/erik/.xpad/xpad.c: In function &#8216;xpad_close&#8217;:
/home/erik/.xpad/xpad.c:408: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/erik/.xpad/xpad.c: In function &#8216;xpad_probe&#8217;:
/home/erik/.xpad/xpad.c:496: error: &#8216;struct input_dev&#8217; has no member named &#8216;cdev&#8217;
/home/erik/.xpad/xpad.c:497: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
make[2]: *** [/home/erik/.xpad/xpad.o] Error 1
make[1]: *** [_module_/home/erik/.xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2

Any ideas what this could mean?

I'm lost :(

---

### Post by guitar_man on 2009-07-01
> **Erik765 said:**
> I plug in my controller, but it doesn't work. FoF, doesn't recognize anything from either of my joysticks when trying to configure keymapping...

I tried the directions from [https://help.ubuntu.com/community/Xbox360Controller]("https://help.ubuntu.com/community/Xbox360Controller")

and when I run make it returns:



Any ideas what this could mean?

I'm lost :(


Are you using jaunty?
Did you configure the keys on the game(FOF)?

---

### Post by Erik765 on 2009-07-01
I have Intrepid at the moment, but will probabaly be upgrading sometime within the next week. Especially if it has built in xpad support.

The only thing FoF lets me configure are keyboard keys. I tried pressing buttons on my other joystick too and it doesn't do anything... Only accepts input from the keyboard.

Anyway, I looked all over and couldn't find a solution to the makefile problem, so I'll probably just upgrade... which is a whole other story ;)

Thanks for your help. ):P

---

### Post by guitar_man on 2009-07-01
Upgrading to jaunty would be the great idea..

Enjoy your game!!!:guitar:

---

