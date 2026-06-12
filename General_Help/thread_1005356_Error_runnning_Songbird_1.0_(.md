---
title: "Error runnning Songbird 1.0 :("
date: 2008-12-08
forum: General Help
---

### Post by ginbuntu on 2008-12-08
I have installed songbird 1.0 using the package I downloaded from getdeb.net but when running songbird I got a invalid pointer error.

```
jin@jin-desktop:~$ songbird 
*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0xb1f210e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d4a3f4]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb1d3d141]
/usr/lib/libvisual-0.4.so.0[0xb1d34407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb1d345e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb1d43ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb1def1f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb408d2c2]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb408db79]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb40987ee]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb4098993]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb4048a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb4048f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb4049589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb4049b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b517e3]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb4047d1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb4047e25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3f13cf3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f1a8e1]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f21252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7610449]
/usr/share/Songbird/xulrunner/libxul.so[0xb760f90b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f1e2ef]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f1e319]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f1dac5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f193a5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3f19b5c]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f1a841]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3f21252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7610449]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fe30f9]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fe3126]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fe29c1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4fcf8b5]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4fcd1e7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4fcd564]
/usr/share/Songbird/xulrunner/libxul.so[0xb75ed21f]
/usr/share/Songbird/xulrunner/libxul.so[0xb75ed7c4]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e82a98]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x1aba)[0xb6e807b2]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7cf1685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:01 321259     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:01 321259     /usr/share/Songbird/songbird-bin
08281000-082a2000 rw-p 08281000 00:00 0          [heap]
b0d88000-b0d90000 rw-p b0d88000 00:00 0 
b1d23000-b1d5f000 r-xp 00000000 08:01 4530631    /usr/lib/libvisual-0.4.so.0.0.0
b1d5f000-b1d60000 r--p 0003b000 08:01 4530631    /usr/lib/libvisual-0.4.so.0.0.0
b1d60000-b1d61000 rw-p 0003c000 08:01 4530631    /usr/lib/libvisual-0.4.so.0.0.0
b1d63000-b1d73000 rw-p b1d63000 00:00 0 
b1d73000-b1de0000 r-xp 00000000 08:01 4532563    /usr/lib/libschroedinger-1.0.so.0.1.0
b1de0000-b1de1000 r--p 0006d000 08:01 4532563    /usr/lib/libschroedinger-1.0.so.0.1.0
b1de1000-b1de2000 rw-p 0006e000 08:01 4532563    /usr/lib/libschroedinger-1.0.so.0.1.0
b1de2000-b1de3000 rw-p b1de2000 00:00 0 
b1ded000-b1df3000 r-xp 00000000 08:01 2310246    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1df3000-b1df4000 r--p 00005000 08:01 2310246    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1df4000-b1df5000 rw-p 00006000 08:01 2310246    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1df5000-b1e0c000 r-xp 00000000 08:01 2310211    /usr/lib/gstreamer-0.10/libgstschro.so
b1e0c000-b1e0d000 r--p 00016000 08:01 2310211    /usr/lib/gstreamer-0.10/libgstschro.so
b1e0d000-b1e0e000 rw-p 00017000 08:01 2310211    /usr/lib/gstreamer-0.10/libgstschro.so
b1e0e000-b1e0f000 rw-p b1e0e000 00:00 0 
b1e0f000-b1e17000 r-xp 00000000 08:01 2310187    /usr/lib/gstreamer-0.10/libgstfaad.so
b1e17000-b1e18000 r--p 00007000 08:01 2310187    /usr/lib/gstreamer-0.10/libgstfaad.so
b1e18000-b1e19000 rw-p 00008000 08:01 2310187    /usr/lib/gstreamer-0.10/libgstfaad.so
b1e19000-b1e3a000 r-xp 00000000 08:01 4532004    /usr/lib/libexif.so.12.2.0
b1e3a000-b1e42000 r--p 00020000 08:01 4532004    /usr/lib/libexif.so.12.2.0
b1e42000-b1e43000 rw-p 00028000 08:01 4532004    /usr/lib/libexif.so.12.2.0
b1e43000-b1eea000 r-xp 00000000 08:01 4532002    /usr/lib/libexempi.so.3.1.3
b1eea000-b1eeb000 r--p 000a7000 08:01 4532002    /usr/lib/libexempi.so.3.1.3
b1eeb000-b1eee000 rw-p 000a8000 08:01 4532002    /usr/lib/libexempi.so.3.1.3
b1ef2000-b1efe000 r-xp 00000000 08:01 2310170    /usr/lib/gstreamer-0.10/libgstannodex.so
b1efe000-b1eff000 r--p 0000b000 08:01 2310170    /usr/lib/gstreamer-0.10/libgstannodex.so
b1eff000-b1f00000 rw-p 0000c000 08:01 2310170    /usr/lib/gstreamer-0.10/libgstannodex.so
b1f00000-b2000000 rw-p b1f00000 00:00 0 
b2000000-b2010000 r-xp 00000000 08:01 2310199    /usr/lib/gstreamer-0.10/libgstmetadata.so
b2010000-b2011000 r--p 0000f000 08:01 2310199    /usr/lib/gstreamer-0.10/libgstmetadata.so
b2011000-b2012000 rw-p 00010000 08:01 2310199    /usr/lib/gstreamer-0.10/libgstmetadata.so
b2012000-b204a000 r-xp 00000000 08:01 4407375    /lib/libncursesw.so.5.6
b204a000-b204d000 rw-p 00037000 08:01 4407375    /lib/libncursesw.so.5.6
b204d000-b20e8000 r-xp 00000000 08:01 4407423    /lib/libslang.so.2.1.3
b20e8000-b20eb000 r--p 0009a000 08:01 4407423    /lib/libslang.so.2.1.3
b20eb000-b20f8000 rw-p 0009d000 08:01 4407423    /lib/libslang.so.2.1.3
b20f8000-b212e000 rw-p b20f8000 00:00 0 
b212e000-b213f000 r-xp 00000000 08:01 4531924    /usr/lib/libcucul.so.0.99.13
b213f000-b2140000 r--p 00010000 08:01 4531924    /usr/lib/libcucul.so.0.99.13
b2140000-b21c7000 rw-p 00011000 08:01 4531924    /usr/lib/libcucul.so.0.99.13
b21c7000-b21cb000 rw-p b21c7000 00:00 0 
b21cb000-b21d3000 r-xp 00000000 08:01 4531874    /usr/lib/libcaca.so.0.99.13
b21d3000-b21d4000 r--p 00007000 08:01 4531874    /usr/lib/libcaca.so.0.99.13
b21d4000-b21d5000 rw-p 00008000 08:01 4531874    /usr/lib/libcaca.so.0.99.13
b21d5000-b21e3000 r-xp 00000000 08:01 4533051    /usr/lib/libid3tag.so.0.3.0
b21e3000-b21e5000 rw-p 0000d000 08:01 4533051    /usr/lib/libid3tag.so.0.3.0
b21e5000-b21fb000 r-xp 00000000 08:01 4533057    /usr/lib/libmad.so.0.2.1
b21fb000-b21fc000 r--p 00015000 08:01 4533057    /usr/lib/libmad.so.0.2.1
b21fc000-b21fd000 rw-p 00016000 08:01 4533057    /usr/lib/libmad.so.0.2.1
b21fe000-b2206000 r-xp 00000000 08:01 4533209    /usr/lib/libiptcdata.so.0.3.2
b2206000-b2208000 rw-p 00007000 08:01 4533209    /usr/lib/libiptcdata.so.0.3.2
b2208000-b220d000 r-xp 00000000 08:01 2310299    /usr/lib/gstreamer-0.10/libgstvmnc.so
b220d000-b220e000 r--p 00004000 08:01 2310299    /usr/lib/gstreamer-0.10/libgstvmnc.so
b220e000-b220f000 rw-p 00005000 08:01 2310299    /usr/lib/gstreamer-0.10/libgstvmnc.so
b220f000-b221f000 r-xp 00000000 08:01 2310162    /usr/lib/gstreamer-0.10/libgstmad.so
b221f000-b2220000 r--p 0000f000 08:01 2310162    /usr/lib/gstreamer-0.10/libgstmad.so
b2220000-b2221000 rw-p 00010000 08:01 2310162    /usr/lib/gstreamer-0.10/libgstmad.so
b2221000-b2230000 r-xp 00000000 08:01 4533062    /usr/lib/libmpcdec.so.3.1.1
b2230000-b2231000 rw-p 0000e000 08:01 4533062    /usr/lib/libmpcdec.so.3.1.1
b2231000-b2237000 rw-p b2231000 00:00 0 
b2237000-b2241000 r-xp 00000000 08:01 2310266    /usr/lib/gstreamer-0.10/libgstinterleave.so
b2241000-b2242000 r--p 00009000 08:01 2310266    /usr/lib/gstreamer-0.10/libgstinterleave.so
b2242000-b2243000 rw-p 0000a000 08:01 2310266    /usr/lib/gstreamer-0.10/libgstinterleave.so
b2243000-b226f000 r-xp 00000000 08:01 4533155    /usr/lib/libdc1394.so.22.1.0
b226f000-b2270000 rw-p 0002b000 08:01 4533155    /usr/lib/libdc1394.so.22.1.0
b2270000-b22b0000 rw-p b2270000 00:00 0 
b22b0000-b22b3000 r-xp 00000000 08:01 2310188    /usr/lib/gstreamer-0.10/libgstfbdevsink.so
b22b3000-b22b4000 r--p 00002000 08:01 2310188    /usr/lib/gstreamer-0.10/libgstfbdevsink.so
b22b4000-b22b5000 rw-p 00003000 08:01 2310188    /usr/lib/gstreamer-0.10/libgstfbdevsink.so
b22b5000-b22b8000 r-xp 00000000 08:01 2310200    /usr/lib/gstreamer-0.10/libgstcacasink.so
b22b8000-b22b9000 r--p 00002000 08:01 2310200    /usr/lib/gstreamer-0.10/libgstcacasink.so
b22b9000-b22ba000 rw-p 00003000 08:01 2310200    /usr/lib/gstreamer-0.10/libgstcacasink.so
b22ba000-b22c0000 r-xp 00000000 08:01 2310206    /usr/lib/gstreamer-0.10/libgstmusepack.so
b22c0000-b22c1000 r--p 00005000 08:01 2310206    /usr/lib/gstreamer-0.10/libgstmusepack

```
My system: Ubuntu Intrepid 32bit
Does any one know how to fix this? Or another way to install Songbird?

thanks in advance

---

### Post by tjwallace on 2008-12-09
My friend is also having similar problems in Ubuntu 8.10 64bit.  Here is the songbird ticket: [http://getsatisfaction.com/songbird/topics/songbird_64_wont_start](http://getsatisfaction.com/songbird/topics/songbird_64_wont_start)

---

### Post by tjwallace on 2008-12-09
I tried the 32bit version of Songbird and it seems to be working properly...

---

### Post by tjwallace on 2008-12-14
This problem may have been caused by the -10 kernel.  Running the -9 kernel does not cause this problem.

---

### Post by s_spiff on 2009-04-14
sudo apt-get remove libvisual-0.4 

Try that out :)

---

### Post by mmssmith on 2009-05-16
Removing libvisual did the trick for me. Thanks!

---

### Post by ibaquez on 2009-11-04
That worked for me until updating to Karmic Koala, then Songbird wont start again

I tryed: sudo apt-get remove libvisual-0.4-0 (moved to libvisual-0.4-0 in KK) but now, it doesnt work

Sorry for the bad news!

---

