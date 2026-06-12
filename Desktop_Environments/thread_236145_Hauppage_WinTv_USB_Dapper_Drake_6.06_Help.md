---
title: "Hauppage WinTv USB Dapper Drake 6.06 Help"
date: 2006-08-14
forum: Desktop Environments
---

### Post by dcotruta on 2006-08-14
I'm a relative newcomer to the Linux scene, but this is the only thing that's really got me stumped.

I'm running 2.6.15-26-686 (for HT support). I want to try and get my WinTV USB card working, but I just can't seem to do it. I tried following the various tutorials for the Hoary release, but when I tried the first step (**make** in the driver folder) this happened:

```
root@catmando-desktop:/home/catmando/Desktop/usbvision-0.9.8.2/src# make
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/catmando/Desktop/usbvision-0.9.8.2/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.o
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:208: error: unknown field ‘name’ specified in initializer
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:208: warning: initialization from incompatible pointer type
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:209: error: unknown field ‘id’ specified in initializer
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:209: error: ‘I2C_ALGO_BIT’ undeclared here (not in a function)
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c: In function ‘i2c_usb_add_bus’:
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:226: error: ‘struct i2c_algorithm’ has no member named ‘id’
make[2]: *** [/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/catmando/Desktop/usbvision-0.9.8.2/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
make: *** [default] Error 2

```

This seemed like a **bad thing**, so I got the next driver (0.9.8.3) and tried that. *Make*, *make install* and *modprobe usbvision* all seemed to work fine, but I don't know where to go from here. 

Zapping crashes out with 
```
VBI initialization failed.
Cannot open '/dev/vbi0': 16, Device or resource busy.
```

XawTv gives me a pretty but useless blue screen with three question marks (???) for the title of the window. 

What I want to know is - has anyone solved this or is this even possible at this point in time.

If not, is there any way (or should I?) "uninstall the usbvision driver?

Thanks in advance for all the help.

---

### Post by John.Michael.Kane on 2006-08-14
This guide is for brezzy,however.the commands should carry over to dapper,and the drivers support your device. [**[COLOR="Red"]WinTV USB**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=114941&highlight=WinTv+USB")

---

### Post by dcotruta on 2006-08-14
Indeed - but why didn't the 0.9.8.2 driver compile? And what is going wrong. It's no use saying the guide works when I've clearly outlined that the first step failed for me.

---

### Post by John.Michael.Kane on 2006-08-14
Note(version 0.9.8.3 can't be compiled under Ubuntu 5.10, you have to download v0.9.8.2) so did you bother trying to compile using v0.9.8.3 ?

---

### Post by dcotruta on 2006-08-14
Maybe I didn't make myself clear.

I'm not running 5.10, but 6.06. I tried compiling 0.9.8.2, but it failed as outlined above.

That, I think, is the issue, but I don't know enough to be able to tell whether it was a dependency problem, or lack of kernel support.

If you can make sense out of the output I got when I tried to compile 0.9.8.2 then maybe I can understand what I've done wrong / what I'm missing (perhaps I just need to try it under a different kernel).

Thanks for the prompt reply.

---

### Post by John.Michael.Kane on 2006-08-14
dcotruta i clearly asked you to try to compile the latest version 0.9.8.3 since 0.9.8.2 may not be compatable with 6.06.

---

### Post by dcotruta on 2006-08-14
My apologies - I think there's been a misunderstanding here.

I **have** compiled 0.9.8.3, and everything seemed to be successful (as far as I can tell, make, make install & modprobe usbvision seemed to work just fine).

The problem is, I don't know what the next step is - as outlined above, 

Zapping crashes out with:
```
VBI initialization failed.
Cannot open '/dev/vbi0': 16, Device or resource busy.
```

Oh, btw, dmesg says the following when I plug the card in:
```
[17206950.764000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17206951.152000] usb 3-1: configuration #1 chosen from 4 choices
[17206951.152000] /home/catmando/Desktop/usbvision/src/usbvision.c: usbvision_probe: Hauppauge WinTv-USB II (PAL) MODEL 566 found
[17206951.152000] /home/catmando/Desktop/usbvision/src/usbvision.c: USBVision[3]: registered USBVision Video device /dev/video0 [v4l]
[17206951.152000] /home/catmando/Desktop/usbvision/src/usbvision.c: USBVision[3]: registered USBVision VBI device /dev/vbi0 [v4l] (Not Working Yet!)
```

The problem is - I don't know what the next step is...

---

### Post by John.Michael.Kane on 2006-08-14
dmesg shows that the device is seen. have you tried installing MythTV or one of the other tv programs. it would seem that zap is having issues with your card. this is just a guess.

---

### Post by dcotruta on 2006-08-14
I think I'm getting to the bottom of the problem.

Zapping fails because it expects DVB information, as do utilities such as scan & scantv.

I don't know whether the problem is that WinTV USB has no DVB support, or whether the driver doesn't support it yet...

I think this
```
[17206951.152000] /home/catmando/Desktop/usbvision/src/usbvision.c: USBVision[3]: registered USBVision VBI device /dev/vbi0 [v4l] (Not Working Yet!)
```
means that the latter is the case.

{edit - i am a moron}
I'm going to post in the sourceforge driver forum, to see if I can get to the bottom of this - if you have any ideas, let me know.

---

### Post by dcotruta on 2006-08-14
OK, nevermind, I seem to be an Idiot. According to the VendorID, this is very clearly a Hauppauge WinTv-USB II (PAL) Model 566. I guess the problem comes from else where.

I've been having a look at the French forums, where these seems to have been quite a lot of discussion about this - but I'm still stumped.

I disabled VBI decoding in zapper - it now starts, but god forbid I should try to tune it. If I start it from the command line I can see an error straight away:
```
** (zapping:13515): WARNING **: GConf key '/apps/zapping/plugins/deinterlace/method' is unset and has no default. Schemas incomplete or not installed?
```

If I click on Channels to try and tune the card it crashes out with
```
(zapping:13515): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(zapping:13515): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(zapping:13515): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(zapping:13515): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(zapping:13515): Gtk-CRITICAL **: gtk_option_menu_set_history: assertion `GTK_IS_OPTION_MENU (option_menu)' failed

(zapping:13515): Gtk-CRITICAL **: gtk_option_menu_set_history: assertion `GTK_IS_OPTION_MENU (option_menu)' failed

(zapping:13515): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

** ERROR **: file keyboard.c: line 251 (get_z_key_entry): assertion failed: (ke != NULL)
aborting...
```

Any ideas?

---

### Post by dcotruta on 2006-08-14
Solved!

I guess that GTK 2.4 broke the Zapper backport. This needs to be fixed - where should I post about this in these forums?

I'm going to submit this as a bug at the Zapper Sourceforge area - is there anything that can be done to fix this from the Ubuntu side?

I'll post a solution in the How To's, but in short it involves installing *kdetv* andplaying around with the settings until it runs.

Thanks for all the help.

---

### Post by John.Michael.Kane on 2006-08-14
You can [**[COLOR="Red"]file bug[/COLOR]**]("https://launchpad.net/distros/ubuntu") reports at the link posted. make sure to include as much info as you can.

---

### Post by Binfarteen on 2006-09-01
> **dcotruta said:**
> Solved!

I guess that GTK 2.4 broke the Zapper backport. This needs to be fixed - where should I post about this in these forums?

I'm going to submit this as a bug at the Zapper Sourceforge area - is there anything that can be done to fix this from the Ubuntu side?

I'll post a solution in the How To's, but in short it involves installing *kdetv* andplaying around with the settings until it runs.

Thanks for all the help.

Can you advise as to which settings make it work?

---

