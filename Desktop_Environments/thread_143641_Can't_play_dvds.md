---
title: "Can't play dvds"
date: 2006-03-12
forum: Desktop Environments
---

### Post by beforewisdom on 2006-03-12
Hi;

I just installed the latest, greatest, again (easyubuntu broke my first install).

I installed dvd decryption keys.

I can't play a DVD with totem.  I booted it from a shell and here is the output I got.

Any help would be appreciated, thanks
----------------------------------------------
steve@00400582fa8a:~$ totem

(totem:10500): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(totem:10500): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

** (totem:10500): CRITICAL **: egg_recent_view_gtk_create_tooltip: assertion `GTK_IS_WIDGET (menu_item)' failed

(totem:10500): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:10500): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: SPACE_1999_4
libdvdnav: DVD Serial Number: 29723288
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/steve/.dvdnav/SPACE_1999_4.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002b56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000b330
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
** Message: don't know how to handle video/mpeg, mpegversion=(int)2, systemstream=(boolean)false
** Message: don't know how to handle audio/x-ac3

---

### Post by codejunkie on 2006-03-12
> **beforewisdom]Hi said:**
> http://dvd.sf.net[/url]
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: SPACE_1999_4
libdvdnav: DVD Serial Number: 29723288
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/steve/.dvdnav/SPACE_1999_4.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002b56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000b330
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
** Message: don't know how to handle video/mpeg, mpegversion=(int)2, systemstream=(boolean)false
** Message: don't know how to handle audio/x-ac3

are you using the totem that came installed by default in ubuntu? if so try installing the package **totem-xine** in synaptic, it seems to work better than totem-gstreamer which is installed by default.

---

### Post by beforewisdom on 2006-03-12
That got it going!

Now, the dvd is playing, but slow and choppy.  I seem to remember from a few years ago that I need to adjust divx or somethng like that for this problem.

Do you know what I should do?

---

### Post by codejunkie on 2006-03-12
[QUOTE=beforewisdom]That got it going!

Now, the dvd is playing, but slow and choppy.  I seem to remember from a few years ago that I need to adjust divx or somethng like that for this problem.

Do you know what I should do?[/QUOTE]
make sure you have dma enabled on your dvddrive, you can check if it's enabled by running hdparm /dev/dvddrive replace ***dvddrive*** with the the actual drive location, for example mine is /dev/hdc you can find that by going into System/Administration/Device Manager under the IDE device sections and the advance tab, if dma is not enabled you can enable it by following this [[COLOR="DarkRed"]**Guide**[/COLOR]]("http://ubuntuguide.org/#speedupcddvdrom") if you have any problems with getting dma enabled just post back here and i'll be happy to help you the best i can.

---

### Post by beforewisdom on 2006-03-12
Got it!

I found my old notes 

=============================
* As root, install the package by to the directory you downloaded to and typing: "dpkg -i libdvdcss2_1.2.4-1_i386.deb"
    * Run Ogle and play the DVD.
    * If your DVD plays but skips and jumps while playing the dvd, then you probably need to enable dma for the drive.
    * To see if dma is enabled, log in as root and type: "/sbin/hdparm -d <device name>" For example: "/sbin/hdparm -d /dev/hdc"
    * To enable dma type: "/sbin/hdparm -d 1 /dev/hdc"
    * If you want dma to be enabled automatically then simply add the line "/sbin/hdparm -d 1 /dev/hdc" to any startup script (/etc/init.d/bootmisc.sh for example).
    * Enjoy watching DVD's in Linux :-)

---

### Post by beforewisdom on 2006-03-12
Ugh, is there anyway to make Totems little "full window" box and control bar at the bottom disappear in full screen mode?

---

### Post by codejunkie on 2006-03-12
[QUOTE=beforewisdom]Ugh, is there anyway to make Totems little "full window" box and control bar at the bottom disappear in full screen mode?[/QUOTE]
they should go away, if you keep the pointer in the center of the screen, if it's placed at the bottom or top of the screen it will open the controls.

---

### Post by dinub1 on 2006-03-12
Well, my Totem-Xine does not want to play a DVDs at all ( a commercial movie). It is stuck on paused and if you press play it gets stuck on pause again, I guess this have to do with copyright, How can I make it play commercially recorded DVD?

---

### Post by codejunkie on 2006-03-12
[QUOTE=dinub1]Well, my Totem-Xine does not want to play a DVDs at all ( a commercial movie). It is stuck on paused and if you press play it gets stuck on pause again, I guess this have to do with copyright, How can I make it play commercially recorded DVD?[/QUOTE]
did it play dvd's in windows?

---

### Post by dinub1 on 2006-03-13
Yes, With Windows Media Player. Alos purchased a program from Orion studios which played under Windows very nicely.

---

### Post by codejunkie on 2006-03-13
[QUOTE=dinub1]Yes, With Windows Media Player. Alos purchased a program from Orion studios which played under Windows very nicely.[/QUOTE]
ok have you installed win32codecs and libdvdcss2? if not you need to before you can play dvd's.

---

