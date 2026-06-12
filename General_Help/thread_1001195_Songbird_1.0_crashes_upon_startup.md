---
title: "Songbird 1.0 crashes upon startup"
date: 2008-12-03
forum: General Help
---

### Post by Jeenyus on 2008-12-03
I installed Songbird 1.0 from the tar.gz file and also from the .deb and keep getting the same error when I start the program 

(crashreporter:7450): Gtk-CRITICAL **:
gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by conjur3r on 2008-12-04
Mine doesn't work either.  Tried both the tar.gz and .deb file.

Outputs the following
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007f60832179a0 ***

with a lot of backtrace.. I'm running a fully patched 8.10 on 64bits

---

### Post by girishven on 2008-12-04
Tried the deb and the tar on 8.10 32 bit. Both give the following error on startup

*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb372a500 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cf13f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7cf3456]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb33e0141]
/usr/lib/libvisual-0.4.so.0[0xb33d7407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb33d75e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb33e6ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb348c1f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb40412c2]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb4041b79]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb404c7ee]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb404c993]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffca44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffcf30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffd589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ffdb44]
.......
......
......
......

and it halts without existing the process.

---

### Post by syko21 on 2008-12-05
Something wrong with Intrepid's glibc I would think since x64 suffers from the same problem

---

### Post by ginbuntu on 2008-12-08
still no fix for this problem?

---

### Post by mc4man on 2008-12-08
I don't see any issue running from the extracted songbird folder, just use 'songbird' not 'songbird-bin'. (either in 8.04 or 8.10 32 bit)

ex. doug@doug-desktop:~/Songbird$ ./songbird

You can easily make yourself a launcher or menu item.

For a good .deb that works on 8.04 or 8.10 ck. here (32 bit and 64 bit versions available

[http://unterhund.wordpress.com/](http://unterhund.wordpress.com/)

---

### Post by ginbuntu on 2008-12-08
that exactly what I did. please my post here [http://ubuntuforums.org/showthread.php?t=1005356&highlight=songbird+error](http://ubuntuforums.org/showthread.php?t=1005356&highlight=songbird+error)

---

### Post by tjwallace on 2008-12-09
My friend is having the same problem on a fully patched 8.10 64bit.  He has selected pre-release updates so maybe I should try rolling this back...
Songbird ticket - [http://getsatisfaction.com/songbird/topics/songbird_64_wont_start](http://getsatisfaction.com/songbird/topics/songbird_64_wont_start)

---

### Post by tjwallace on 2008-12-09
I tried the 32bit version of Songbird and it seems to be working properly...

---

### Post by conjur3r on 2008-12-11
Nice.  I just tried the 32bit deb from getdeb on my 64bit OS and it's working fine.  You can install it with:

# sudo dpkg -i --force-architecture songbird_1.0.0-0~getdeb1_i386.deb

---

