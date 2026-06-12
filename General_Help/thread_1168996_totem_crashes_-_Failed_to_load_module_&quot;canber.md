---
title: "totem crashes - Failed to load module &quot;canberra-gtk-module&quot;"
date: 2009-05-24
forum: General Help
---

### Post by orengolan on 2009-05-24
Totem don't play anything and crashes.
here is the error.  any ideas?

Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

** (totem:16267): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 76 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Failed to receive messages at scim_bridge_client_read_and_dispatch ()
An IOException occurred at handle_message ()
*** glibc detected *** totem: double free or corruption (fasttop): 0x0a2bb9f0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6f9d604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb6f9f5b6]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim-bridge.so(scim_bridge_free_messenger+0x52)[0xb4f1c892]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim-bridge.so(scim_bridge_client_close_messenger+0x3b)[0xb4f1e92b]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim-bridge.so(scim_bridge_client_finalize+0x42)[0xb4f211e2]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim-bridge.so(scim_bridge_client_gtk_finalize+0x41)[0xb4f18441]
/lib/tls/i686/cmov/libc.so.6(exit+0x89)[0xb6f5cbb9]
/usr/lib/libgdk-x11-2.0.so.0[0xb755b647]
/usr/lib/libX11.so.6(_XError+0x109)[0xb70cadb9]
/usr/lib/libX11.so.6[0xb70d2638]
/usr/lib/libX11.so.6(_XReply+0x10d)[0xb70d2ccd]
/usr/lib/libX11.so.6(XSync+0x67)[0xb70c6507]
/usr/lib/gstreamer-0.10/libgstxvimagesink.so[0xb5ec09e3]
/usr/lib/gstreamer-0.10/libgstxvimagesink.so[0xb5ec10f3]
/usr/lib/libgstbase-0.10.so.0[0xb7ecbdf4]
/usr/lib/libgstbase-0.10.so.0[0xb7ecc20d]
/usr/lib/libgstbase-0.10.so.0[0xb7ecc725]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstreamer-0.10.so.0[0xb7e0131d]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstreamer-0.10.so.0[0xb7e0131d]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstreamer-0.10.so.0[0xb7e0131d]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstbase-0.10.so.0[0xb7edfcaf]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstbase-0.10.so.0[0xb7edfcaf]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstbase-0.10.so.0[0xb7edfcaf]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstreamer-0.10.so.0[0xb7e0131d]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstreamer-0.10.so.0[0xb7e0131d]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstbase-0.10.so.0[0xb7edfcaf]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/gstreamer-0.10/libgstgoom.so[0xb4eefe9a]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstreamer-0.10.so.0[0xb7e0131d]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstbase-0.10.so.0[0xb7edfcaf]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstbase-0.10.so.0[0xb7edfcaf]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/libgstbase-0.10.so.0[0xb7edfcaf]
/usr/lib/libgstreamer-0.10.so.0[0xb7e10ac5]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push+0x33a)[0xb7e11eba]
/usr/lib/gstreamer-0.10/libgstcoreelements.so[0xb5eef1a2]
/usr/lib/libgstreamer-0.10.so.0[0xb7e33593]
======= Memory map: ========
08048000-080ad000 r-xp 00000000 08:01 1094342    /usr/bin/totem-gstreamer
080ad000-080ae000 r--p 00064000 08:01 1094342    /usr/bin/totem-gstreamer
080ae000-080b0000 rw-p 00065000 08:01 1094342    /usr/bin/totem-gstreamer
0974e000-0a753000 rw-p 0974e000 00:00 0          [heap]
b1b78000-b1b9c000 rw-s 00000000 00:09 12517405   /SYSV00000000 (deleted)
b1b9c000-b1b9d000 ---p b1b9c000 00:00 0 
b1b9d000-b26f1000 rw-p b1b9d000 00:00 0 
b26f1000-b26f2000 ---p b26f1000 00:00 0 
b26f2000-b2ef2000 rw-p b26f2000 00:00 0 
b2ef2000-b2ef3000 ---p b2ef2000 00:00 0 
b2ef3000-b36f3000 rw-p b2ef3000 00:00 0 
b36f3000-b36f4000 ---p b36f3000 00:00 0 
b36f4000-b3ef4000 rw-p b36f4000 00:00 0 
b3ef4000-b3f80000 r--p 00000000 08:01 1122953    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3f80000-b4000000 r--p 00000000 08:01 1123638    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b4000000-b407b000 rw-p b4000000 00:00 0 
b407b000-b4100000 ---p b407b000 00:00 0 
b4104000-b4111000 r-xp 00000000 08:01 49212      /lib/libgcc_s.so.1
b4111000-b4112000 r--p 0000c000 08:01 49212      /lib/libgcc_s.so.1
b4112000-b4113000 rw-p 0000d000 08:01 49212      /lib/libgcc_s.so.1
b4113000-b4155000 rw-p b4113000 00:00 0 
b4155000-b4174000 r-xp 00000000 08:01 1094506    /usr/lib/libjpeg.so.62.0.0
b4174000-b4175000 rw-p 0001e000 08:01 1094506    /usr/lib/libjpeg.so.62.0.0
b4181000-b418b000 r-xp 00000000 08:01 1255798    /usr/lib/gstreamer-0.10/libgstvideoscale.so
b418b000-b418c000 r--p 00009000 08:01 1255798    /usr/lib/gstreamer-0.10/libgstvideoscale.so
b418c000-b418d000 rw-p 0000a000 08:01 1255798    /usr/lib/gstreamer-0.10/libgstvideoscale.so
b418d000-b41bb000 r-xp 00000000 08:01 1255171    /usr/lib/gstreamer-0.10/libgstffmpegcolorspace.so
b41bb000-b41bc000 r--p 0002d000 08:01 1255171    /usr/lib/gstreamer-0.10/libgstffmpegcolorspace.so
b41bc000-b41bd000 rw-p 0002e000 08:01 12551Aborted

---

