---
title: "Complete Freeze!"
date: 2011-01-20
forum: Desktop Environments
---

### Post by Drigy on 2011-01-20
Hi,

when I go to Ubuntu desktop, it freezes after 3-4 minutes. As it freezes the screen gets a broken line across it (picture added).

When i go to KDE desktop or if i go to Ubuntu under root everzthing is okay.
I have ATI GPU =/

Please help!

---

### Post by sanderd17 on 2011-01-20
I think it is compiz that can't work with your graphical card. You chould disable all graphical effects and probably remove docky too.

If compiz can't work with your graphical card, there's not much to do about it. The only thing you can do is wait for a new driver on the next ubuntu release.

---

### Post by Krytarik on 2011-01-21
Make sure you have the best available driver for your video card installed and running.

What video card do you have precisely, what driver are you running?

---

### Post by Drigy on 2011-01-21
Here's the thing. I used metacity --replace command to disable compiz. It worked for a while but the desktop was always busy. I know that because it hadn't had any icons and mouse was busy (dial-pad rolling like a sand clock in windows).
Next time a started Ubuntu the login screen didn't show but it was there and i was able to login blindly. Then after 30sec it kicked me back to the login screen which was still blank. 
Next time I started Ubuntu nothing happened after the GRUB menu dissapeared, it was all blank.

All things are in a chronological order. 

Couple of minutes ago i managed to get into Ubuntu, don't know how or why. I guess it has something to do with ATI fglrx that I use. Mouse still dialing though :? I'm "shaking in fear" that system will collapse any second :shock:

Thank you for your replys folks.

Oh..I have 5450HD.

---

### Post by Drigy on 2011-01-21
And the problem remains. After GRUB there is no DVI-D input available

---

### Post by Krytarik on 2011-01-21
Since you said that KDE is working fine, the issue seems to be confined to Gnome and/or your user profile (regarding Gnome specific config).

Check ~/.xsession-errors and /var/log/Xorg.0.log for error messages.

---

### Post by endotherm on 2011-01-21
just an aside, when your system locks, if you want to shut it down gracefully (unmount disks etc), try the magic sysreq

[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

hold down Alt + Prntscrn/SysReq and slowly type:
```
reisub
```
when you get to 's', the hdd access light on your pc case may come on. wait until it is off again before proceding to 'u'.
s is for 'synch' and it writes all pending unwritten data in the buffers to your disk. u then unmounts the volumes (among other things.)

---

### Post by Drigy on 2011-01-22
As it appears the problem is in fglrx drivers. Now running without. Nautilus also stopped working under fglrx (segmentation problem)```
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 124 error_code 1 request_code 136 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

And my ~/.xsession-errors output 
```
(nm-applet:1858): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nm-applet:1858): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-applet:1858): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed

(nm-applet:1858): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nm-applet:1858): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-applet:1858): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed
```

I'll wait for fglrx updates. If indeed it is a bug.
Thank you!!

---

### Post by Krytarik on 2011-01-22
I guess the logged xsession-errors aren't really critical, but the Nautilus error is.

You might try the PPA of Ubuntu-X-Swat, they allegedly update their driver packages pretty fast, also building them from the proprietary drivers:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by Drigy on 2011-01-28
The PPA you provided worked quite alright, thanks. Still had some problems though.
After todays kernel upgrade and other updates everything is back to normal. Now i can watch flash videos with hardware support.

Thanks again!

---

