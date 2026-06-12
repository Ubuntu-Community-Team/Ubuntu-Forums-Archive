---
title: "allowing file access in multiple accounts"
date: 2009-04-12
forum: General Help
---

### Post by AvengingAngel718 on 2009-04-12
i have a guest account on my computer that i would like to have access to files and programs contained within my administrative account. is there a way i can allow access to things without painstakingly going through and changing permissions on everything? i have a symbolic link to the files i want access to in the guest's home folder, but there's also a few programs such as mozilla songbird and google earth installed under the administrator profile that show up in the menu but won't start in the guest profile.

---

### Post by defaultusername on 2009-04-12
AvengingAngel718,

chmod/chown/chgrp all have -R switches for recursive directory traversal. Software installed by apt-get/Synaptic shouldn't have permission issues with a user account by default. If a new user is having trouble, add the username to the appropriate group. Perhaps you missed on some basic system configuration when you were installing Ubuntu?

---

### Post by AvengingAngel718 on 2009-04-12
not sure... i switched all the permissions after i posted so that wasnt really a problem, the only issue is with songbird. it wasn't available through apt so i installed it from the deb package...but all other software i installed that way works in the guest account

---

### Post by AvengingAngel718 on 2009-04-12
i guess i should explain the problem a bit more. when i click the songbird icon the program begins loading but doesnt actually start up. I found every file and folder i could that was associated with songbird and changed the permissions but it still doesnt start. it's not a huge deal because i can just use rhythmbox but it's really annoying

---

### Post by defaultusername on 2009-04-12
AvengingAngel718,

Go into a terminal and execute Songbird. Post the output (if any). strace is also useful for tracing syscalls/signals occuring that might lead to an answer.

---

### Post by AvengingAngel718 on 2009-04-12
*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0x00007f77c2de0980 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f77f0be9a58]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7f77bb58b4ce]
/usr/lib/libvisual-0.4.so.0[0x7f77bb584646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7f77bb5847d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7f77bb591703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7f77bb7b2c24]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f77df0a132a]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x64b)[0x7f77df0a1be3]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f77df0abf41]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7f77df0ac0c4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f77df05c7a5]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f77df05cc13]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f77df05d1cf]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f77df05d753]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x528)[0x7f77ecf62908]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7f77df05bb56]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7f77df05bc43]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7f77dccfdcb8]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f77dcd04de9]
/usr/share/Songbird/xulrunner/libxul.so[0x7f77eea99e7f]
/usr/share/Songbird/xulrunner/libxul.so[0x7f77eea999c9]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f77dcd0a66b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f77dcd0a698]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f77dcd09e80]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f77dcd03aaa]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7f77dcd04039]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f77dcd04d59]
/usr/share/Songbird/xulrunner/libxul.so[0x7f77eea99e7f]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f77e1c6ba9f]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f77e1c6badc]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f77e1c6b3be]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7f77e1c57a24]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7f77e1c559cb]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f77e1c55da0]
/usr/share/Songbird/xulrunner/libxul.so[0x7f77eea7a79a]
/usr/share/Songbird/xulrunner/libxul.so[0x7f77eea7ac6c]
/usr/share/Songbird/xulrunner/libxul.so[0x7f77ee34fc76]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7f77ee34d947]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f77f0b8e466]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:11 3631280                            /usr/share/Songbird/songbird-bin
00608000-00609000 rw-p 00008000 08:11 3631280                            /usr/share/Songbird/songbird-bin
00e10000-00e31000 rw-p 00e10000 00:00 0                                  [heap]
41f2c000-41f2d000 ---p 41f2c000 00:00 0 
41f2d000-4272d000 rwxp 41f2d000 00:00 0 
4272d000-4272e000 ---p 4272d000 00:00 0 
4272e000-42f2e000 rwxp 4272e000 00:00 0 
7f77b9bac000-7f77b9bad000 r-xp 00000000 08:11 3311216                    /usr/lib/tls/libnvidia-tls.so.180.11
7f77b9bad000-7f77b9cad000 ---p 00001000 08:11 3311216                    /usr/lib/tls/libnvidia-tls.so.180.11
7f77b9cad000-7f77b9cae000 rw-p 00001000 08:11 3311216                    /usr/lib/tls/libnvidia-tls.so.180.11
7f77bb572000-7f77bb5af000 r-xp 00000000 08:11 3280350                    /usr/lib/libvisual-0.4.so.0.0.0
7f77bb5af000-7f77bb7ae000 ---p 0003d000 08:11 3280350                    /usr/lib/libvisual-0.4.so.0.0.0
7f77bb7ae000-7f77bb7af000 r--p 0003c000 08:11 3280350                    /usr/lib/libvisual-0.4.so.0.0.0
7f77bb7af000-7f77bb7b0000 rw-p 0003d000 08:11 3280350                    /usr/lib/libvisual-0.4.so.0.0.0
7f77bb7b0000-7f77bb7b6000 r-xp 00000000 08:11 37544777                   /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f77bb7b6000-7f77bb9b5000 ---p 00006000 08:11 37544777                   /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f77bb9b5000-7f77bb9b6000 r--p 00005000 08:11 37544777                   /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f77bb9b6000-7f77bb9b7000 rw-p 00006000 08:11 37544777                   /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f77bb9b7000-7f77bb9cc000 r-xp 00000000 08:11 3278472                    /usr/lib/libmpeg2.so.0.0.0
7f77bb9cc000-7f77bbbcb000 ---p 00015000 08:11 3278472                    /usr/lib/libmpeg2.so.0.0.0
7f77bbbcb000-7f77bbbcc000 rw-p 00014000 08:11 3278472                    /usr/lib/libmpeg2.so.0.0.0
7f77bbbcc000-7f77bbbce000 rw-p 7f77bbbcc000 00:00 0 
7f77bbbce000-7f77bbbd7000 r-xp 00000000 08:11 3293940                    /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
7f77bbbd7000-7f77bbdd6000 ---p 00009000 08:11 3293940                    /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
7f77bbdd6000-7f77bbdd7000 r--p 00008000 08:11 3293940                    /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
7f77bbdd7000-7f77bbdd8000 rw-p 00009000 08:11 3293940                    /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
7f77bbdd8000-7f77bbde4000 r-xp 00000000 08:11 37544822                   /usr/lib/gstreamer-0.10/libgstspeex.so
7f77bbde4000-7f77bbfe3000 ---p 0000c000 08:11 37544822                   /usr/lib/gstreamer-0.10/libgstspeex.so
7f77bbfe3000-7f77bbfe4000 r--p 0000b000 08:11 37544822                   /usr/lib/gstreamer-0.10/libgstspeex.so
7f77bbfe4000-7f77bbfe5000 rw-p 0000c000 08:11 37544822                   /usr/lib/gstreamer-0.10/libgstspeex.so
7f77bbfe5000-7f77bbfe8000 r-xp 00000000 08:11 3278752                    /usr/lib/libBPM.so.1.0.0
7f77bbfe8000-7f77bc1e7000 ---p 00003000 08:11 3278752                    /usr/lib/libBPM.so.1.0.0
7f77bc1e7000-7f77bc1e9000 rw-p 00002000 08:11 3278752                    /usr/lib/libBPM.so.1.0.0
7f77bc1e9000-7f77bc1f5000 r-xp 00000000 08:11 3278753                    /usr/lib/libSoundTouch.so.1.0.0
7f77bc1f5000-7f77bc3f5000 ---p 0000c000 08:11 3278753                    /usr/lib/libSoundTouch.so.1.0.0
7f77bc3f5000-7f77bc3f7000 rw-p 0000c000 08:11 3278753                    /usr/lib/libSoundTouch.so.1.0.0
7f77bc3f7000-7f77bc3ff000 r-xp 00000000 08:11 37544755                   /usr/lib/gstreamer-0.10/libgstsoundtouch.so
7f77bc3ff000-7f77bc5fe000 ---p 00008000 08:11 37544755                   /usr/lib/gstreamer-0.10/libgstsoundtouch.so
7f77bc5fe000-7f77bc5ff000 r--p 00007000 08:11 37544755                   /usr/lib/gstreamer-0.10/libgstsoundtouch.so
7f77bc5ff000-7f77bc600000 rw-p 00008000 08:11 37544755                   /usr/lib/gstreamer-0.10/libgstsoundtouch.so
7f77bc600000-7f77bc700000 rw-p 7f77bc600000 00:00 0 
7f77bc7cd000-7f77bc7dc000 r-xp 00000000 08:11 3278756                    /usr/lib/libWildMidi.so.0.0.0
7f77bc7dc000-7f77bc9db000 ---p 0000f000 08:11 3278756                    /usr/lib/libWildMidi.so.0.0.0
7f77bc9db000-7f77bc9df000 rw-p 0000e000 08:11 3278756                    /usr/lib/libWildMidi.so.0.0.0
7f77bc9df000-7f77bc9e8000 rw-p 7f77bc9df000 00:00 0 
7f77bc9e8000-7f77bc9ee000 r-xp 00000000 08:11 37544765                   /usr/lib/gstreamer-0.10/libgstwildmidi.so
7f77bc9ee000-7f77bcbed000 ---p 00006000 08:11 37544765                   /usr/lib/gstreamer-0.10/libgstwildmidi.so
7f77bcbed000-7f77bcbee000 r--p 00005000 08:11 37544765                   /usr/lib/gstreamer-0.10/libgstwildmidi.so
7f77bcbee000-7f77bcbef000 rw-p 00006000 08:11 37544765                   /usr/lib/gstreamer-0.10/libgstwildmidi.so
7f77bcbef000-7f77bcbf8000 r-xp 00000000 08:11 37544797                   /usr/lib/gstreamer-0.10/libgstgdkpixbuf.so
7f77bcbf8000-7f77bcdf7000 ---p 00009000 08:11 37544797                   /usr/lib/gstreamer-0.10/libgstgdkpixbuf.so
7f77bcdf7000-7f77bcdf8000 r--p 00008000 08:11 37544797                   /usr/lib/gstreamer-0.10/libgstgdkpixbuf.so
7f77bcdf8000-7f77bcdf9000 rw-p 00009000 08:11 37544797                   /usr/lib/gstreamer-0.10/libgstgdkpixbuf.so
7f77bcdf9000-7f77bcdfd000 r-xp 00000000 08:11 37544807                   /usr/lib/gstreamer-0.10/libgstmonoscope.so
7f77bcdfd000-7f77bcffc000 ---p 00004000 08:11 37544807                   /usr/lib/gstreamer-0.10/libgstmonoscope.so
7f77bcffc000-7f77bcffd000 r--p 00003000 08:11 37544807                   /usr/lib/gstreamer-0.10/libgstmonoscope.so
7f77bcffd000-7f77bcffe000 rw-p 00004000 08:11 37544807                   /usr/lib/gstreamer-0.10/libgstmonoscope.so
7f77bcffe000-7f77bd007000 r-xp 00000000 08:11 37544724                   /usr/lib/gstreamer-0.10/libgstdvdspu.so
7f77bd007000-7f77bd206000 ---p 00009000 08:11 37544724                   /usr/lib/gstreamer-0.10/libgstdvdspu.so
7f77bd206000-7f77bd207000 r--p 00008000 08:11 37544724               Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

