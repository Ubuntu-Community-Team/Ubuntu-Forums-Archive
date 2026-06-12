---
title: "First time using 360 Controller in Ubu: Suggestions?"
date: 2013-08-09
forum: Gaming &amp; Leisure
---

### Post by rjsec4ever on 2013-08-09
Topic Question.
Haven't used the controller on any Ubuntu version. What do I need to do to get it to work properly?

---

### Post by Kjellson on 2013-08-10
You should not need to do anything at all. (except to plug it in) I have used two wired 360 controllers on Linux Mint, and they work out of the box. I don´t have any experience from the wireless one though.
It´s kinda ironic actually, in order to use the controller on Windows, one has to download drivers for it, but in Linux there´s no need for drivers.

---

### Post by mirearts KING SUNNY on 2013-08-10
It is automatic, just plug the usb and it is automatically assigned.

---

### Post by DarkAmbient on 2013-08-12
A wired one is fully functional (except the "led-light" around the xbox-button) the moment you hook it in.  Point out that a wireless controller using a charging-cable is still a wireless one.. the cable does nothing more than charging.

A wireless one (using a wireless reciever) works perfectly as a controller when running xboxdrv (as root).

With games like Dungeon Defenders which requires a Xbox360 controller, doesn't seem to acknowledge a wireless controller as a 360 one. To be able to play using a wireless you need to add quite a few parameters when running xboxdrv. I got my 4 wireless to work with DD after a while of testing.  I'm unable to provide the xboxdrv-command right now, as the computer and the controllers stayed at my ex-gf:s apartment.

But If you need help with wireless ones to play Trine or DD with, let me know. :)

---

### Post by danirv81-1 on 2013-09-30
In most cases the controllers are plug and play, i know that in Ubuntu 13.04 there is a problem with the axis mapping and so you have to manually map the controller in xboxdrv, my preferred config is this, and is also the script I have to use every time I plug it in -_-

sudo rmmod xmap
sudo xboxdrv --ui-axismap x2=REL_X:10,y2=REL_Y:10,x1=KEY_Q:KEY_D,y1=KEY_W:KEY_S --ui-buttonmap a=KEY_A,b=KEY_B,x=KEY_X,y=KEY_Y --ui-buttonmap lb=KEY_L,rb=KEY_R --trigger-as-button --ui-buttonmap lt=KEY_F,rt=KEY_G --ui-buttonmap dl=KEY_4,dr=KEY_2,du=REL_WHEEL:-1:150,dd=REL_WHEEL:1:150 --ui-buttonmap back=KEY_TAB,start=KEY_ESC -s --deadzone 6000 --dpad-as-button --autofire rt=1 --autofire lt=1 --ui-buttonmap tl=KEY_N,tr=KEY_M

---

### Post by Ranko Kohime on 2013-10-01
> **danirv81-1 said:**
> sudo rmmod xmap
The default kernel module is **xpad**, just so nobody is confused.  :)

If you use xboxdrv regularly, you can add xpad to the kernel module blacklist: /etc/modprobe.d/blacklist.conf

---

