---
title: "Warsow &amp; Second life NOT working"
date: 2007-05-29
forum: Gaming &amp; Leisure
---

### Post by leopard6661 on 2007-05-29
I recently installed second life and after it loads all I get is a black window, then nothing, I have to force quit it
Then I tried warsow, and all I get this time is sounds and no visual!!! Nothing cant exit, cant get anything else to work and I have to reset my computer
i am guessing this is a video driver related problem but how to solve it, I have Nvidia 6200 and I installed the driver, everything else is working, beryl is working so what is the problem
thanks in advance


I got warsow to work, but second life

---

### Post by Toxicity999 on 2007-05-29
Try running either of these through the  terminal, with beryl off. If it still doesn't work, get back here with the error output.

---

### Post by leopard6661 on 2007-05-29
Warsow did work, but here is what happened when I tried to run Second life from the terminal, I got the black screen and nothing
I dont know what is the error output, but here is what the terminal wrote:



GL_NV_texture_shader3
GL_NV_vertex_array_range
GL_NV_vertex_array_range2
GL_NV_vertex_program
GL_NV_vertex_program1_1
GL_NV_vertex_program2
GL_NV_vertex_program2_option
GL_NV_vertex_program3
GL_NVX_conditional_render
GL_SGIS_generate_mipmap
GL_SGIS_texture_lod
GL_SGIX_depth_texture
GL_SGIX_shadow
GL_SUN_slice_accum




2007-05-29T20:33:41Z INFO: main: Viewer Digest: 4b69dc56-641a-da4f-d688-fa1bd47cb07b
2007-05-29T20:33:41Z INFO: dump: Resend: 75
2007-05-29T20:33:41Z INFO: dump: Land: 85
2007-05-29T20:33:41Z INFO: dump: Wind: 17
2007-05-29T20:33:41Z INFO: dump: Cloud: 17
2007-05-29T20:33:41Z INFO: dump: Task: 223
2007-05-29T20:33:41Z INFO: dump: Texture: 223
2007-05-29T20:33:41Z INFO: dump: Asset: 110
2007-05-29T20:33:41Z INFO: dump: Total: 750
2007-05-29T20:33:41Z INFO: idle_startup: Initializing messaging system...
2007-05-29T20:33:41Z INFO: loadFile: Loading message.xml file at /home/mohamed/.Games/SecondLife/app_settings/message.xml
2007-05-29T20:33:41Z INFO: initClass: LLMessageConfig::intiClass config file /home/mohamed/.Games/SecondLife/app_settings/message.xml
2007-05-29T20:33:41Z INFO: loadTemplateFile: Message template checksum = bff807b2
2007-05-29T20:33:41Z INFO: start_net: startNet - receive buffer size : 262142
2007-05-29T20:33:41Z INFO: start_net: startNet - send buffer size    : 262142
2007-05-29T20:33:41Z INFO: start_messaging_system: Message template version matches prehash version number
2007-05-29T20:33:41Z INFO: setAckThrottleBPS: LLXferManager ack throttle min rate: 2.66667e+06
2007-05-29T20:33:41Z INFO: setAckThrottleBPS: LLXferManager ack throttle actual rate: 2.93333e+06
2007-05-29T20:33:41Z INFO: setAckThrottleBPS: LLXferManager ack throttle min rate: 8000
2007-05-29T20:33:41Z INFO: setAckThrottleBPS: LLXferManager ack throttle actual rate: 150000
2007-05-29T20:33:41Z INFO: setUpstream: AssetStorage: Setting upstream provider to 0.0.0.0:12036
2007-05-29T20:33:41Z INFO: idle_startup: Initializing embedded web browser...
2007-05-29T20:33:41Z INFO: LLAudioEngine_FMOD::init() initializing FMOD
2007-05-29T20:33:41Z INFO: init: Trying ESD audio output...
2007-05-29T20:33:41Z INFO: ESD audio output initialized OKAY
2007-05-29T20:33:41Z INFO: init: Audio output: ESD
2007-05-29T20:33:41Z INFO: LLAudioEngine_FMOD::init() FMOD initialized correctly
2007-05-29T20:33:41Z INFO: idle_startup: Initializing Window
2007-05-29T20:33:41Z INFO: login_show: Initializing Login Screen
*** glibc detected *** bin/do-not-directly-run-secondlife-bin: double free or corruption (out): 0x0cc82598 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb64f07cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb64f3e30]
/home/mohamed/.Games/SecondLife/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb66a68b1]
/usr/lib/libscim-1.0.so.8[0xabeef156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xabeeff77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xabeeaf05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xabf80f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb6301b41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb62e81cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb62e85ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb62e87a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xabf75b57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xabf8527c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb7d8bd29]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d8c93b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d8cb39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb7d89f0e]
/home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxul.so(_ZN8nsWindow16IMECreateContextEv+0x52)[0xb7946100]
/home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxul.so(_ZN8nsWindow12NativeCreateEP9nsIWidgetPvRK6nsRectPF13nsEventStatusP10nsGUIEventEP16nsIDeviceContextP11nsIAppShellP10nsIToolkitP16nsWidgetInitData+0xef1)[0xb7942ca7]
/home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxul.so[0xb793e45c]
/home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxul.so[0xb777b35a]
bin/do-not-directly-run-secondlife-bin[0x9a21a41]
bin/do-not-directly-run-secondlife-bin[0x9a1fa3a]
bin/do-not-directly-run-secondlife-bin[0x9a1fafa]
bin/do-not-directly-run-secondlife-bin[0x9a1e558]
bin/do-not-directly-run-secondlife-bin[0x956b0af]
bin/do-not-directly-run-secondlife-bin[0x956b680]
bin/do-not-directly-run-secondlife-bin[0x9885196]
bin/do-not-directly-run-secondlife-bin[0x988395c]
bin/do-not-directly-run-secondlife-bin[0x97f0e58]
bin/do-not-directly-run-secondlife-bin[0x98876e4]
bin/do-not-directly-run-secondlife-bin[0x8cbe568]
bin/do-not-directly-run-secondlife-bin[0x8cbfd39]
bin/do-not-directly-run-secondlife-bin[0x8eda1aa]
bin/do-not-directly-run-secondlife-bin[0x8ee04c9]
bin/do-not-directly-run-secondlife-bin[0x9627a45]
bin/do-not-directly-run-secondlife-bin[0x9629bfc]
bin/do-not-directly-run-secondlife-bin[0x962c4f1]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb649eebc]
bin/do-not-directly-run-secondlife-bin(__gxx_personality_v0+0x1fd)[0x805c1f1]
======= Memory map: ========
08048000-09b73000 r-xp 00000000 08:11 423528     /home/mohamed/.Games/SecondLife/bin/do-not-directly-run-secondlife-bin
09b73000-09d08000 rwxp 01b2b000 08:11 423528     /home/mohamed/.Games/SecondLife/bin/do-not-directly-run-secondlife-bin
09d08000-0cd47000 rwxp 09d08000 00:00 0          [heap]
abd00000-abd21000 rwxp abd00000 00:00 0 
abd21000-abe00000 ---p abd21000 00:00 0 
abe87000-abf5b000 r-xp 00000000 08:11 506850     /usr/lib/libscim-1.0.so.8.1.0
abf5b000-abf69000 rwxp 000d4000 08:11 506850     /usr/lib/libscim-1.0.so.8.1.0
abf69000-abf8a000 r-xp 00000000 08:11 48919      /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
abf8a000-abf8b000 rwxp 00021000 08:11 48919      /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
abf8b000-abf8c000 ---p abf8b000 00:00 0 
abf8c000-ac78c000 rwxp abf8c000 00:00 0 
ac78c000-ac78d000 ---p ac78c000 00:00 0 
ac78d000-acf8d000 rwxp ac78d000 00:00 0 
acf8d000-ad04d000 r-xp 00000000 08:11 506267     /usr/lib/libasound.so.2.0.0
ad04d000-ad052000 rwxp 000bf000 08:11 506267     /usr/lib/libasound.so.2.0.0
ad052000-ad072000 r-xp 00000000 08:11 506279     /usr/lib/libaudiofile.so.0.0.2
ad072000-ad074000 rwxp 00020000 08:11 506279     /usr/lib/libaudiofile.so.0.0.2
ad074000-ad07d000 r-xp 00000000 08:11 506389     /usr/lib/libesd.so.0.2.36
ad07d000-ad07e000 rwxp 00009000 08:11 506389     /usr/lib/libesd.so.0.2.36
ad07e000-ad082000 r-xp 00000000 08:11 506607     /usr/lib/libgthread-2.0.so.0.1200.11
ad082000-ad083000 rwxp 00003000 08:11 506607     /usr/lib/libgthread-2.0.so.0.1200.11
ad083000-ad0cc000 r-xp 00000000 08:11 506184     /usr/lib/libORBit-2.so.0.1.0
ad0cc000-ad0d6000 rwxp 00048000 08:11 506184     /usr/lib/libORBit-2.so.0.1.0
ad0d6000-ad105000 r-xp 00000000 08:11 506441     /usr/lib/libgconf-2.so.4.1.2
ad105000-ad108000 rwxp 0002e000 08:11 506441     /usr/lib/libgconf-2.so.4.1.2
ad117000-ad11d000 r-xp 00000000 08:11 235878     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/components/libsystem-pref.so
ad11d000-ad11e000 rwxp 00005000 08:11 235878     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/components/libsystem-pref.so
ad11e000-ad11f000 ---p ad11e000 00:00 0 
ad11f000-ad91f000 rwxp ad11f000 00:00 0 
ad91f000-ad95a000 r-xp 00000000 08:11 49901      /usr/lib/locale/en_US.utf8/LC_CTYPE
ad95a000-ad95b000 r-xp 00000000 08:11 49906      /usr/lib/locale/en_US.utf8/LC_NUMERIC
ad95b000-ad95c000 r-xp 00000000 08:11 49909      /usr/lib/locale/en_US.utf8/LC_TIME
ad95c000-ada33000 r-xp 00000000 08:11 49900      /usr/lib/locale/en_US.utf8/LC_COLLATE
ada33000-ada34000 r-xp 00000000 08:11 49904      /usr/lib/locale/en_US.utf8/LC_MONETARY
ada34000-ada35000 r-xp 00000000 08:11 49910      /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
ada35000-ada36000 r-xp 00000000 08:11 49907      /usr/lib/locale/en_US.utf8/LC_PAPER
ada36000-ada37000 r-xp 00000000 08:11 49905      /usr/lib/locale/en_US.utf8/LC_NAME
ada37000-ada38000 r-xp 00000000 08:11 49899      /usr/lib/locale/en_US.utf8/LC_ADDRESS
ada38000-ada39000 r-xp 00000000 08:11 49908      /usr/lib/locale/en_US.utf8/LC_TELEPHONE
ada39000-ada3a000 r-xp 00000000 08:11 49903      /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
ada3a000-ada3b000 r-xp 00000000 08:11 49902      /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
ada3b000-adc3b000 rwxs e0f1f000 00:0d 17241      /dev/nvidia0
adc3b000-add3d000 rwxp adc3b000 00:00 0 
add3d000-add4a000 r-xp 00000000 08:11 423524     /home/mohamed/.Games/SecondLife/fonts/MtBdLfRg.ttf
add4a000-ae5d8000 r-xp 00000000 08:11 182439     /usr/share/fonts/truetype/kochi/kochi-mincho-subst.ttf
ae5d8000-ae6da000 rwxp ae5d8000 00:00 0 
ae6da000-ae6e8000 r-xp 00000000 08:11 423523     /home/mohamed/.Games/SecondLife/fonts/MtBkLfRg.ttf
ae6e8000-aef76000 r-xp 00000000 08:11 182439     /usr/share/fonts/truetype/kochi/kochi-mincho-subst.ttf
aef76000-af078000 rwxp aef76000 00:00 0 
af078000-af086000 r-xp 00000000 08:11 423523     /home/mohamed/.Games/SecondLife/fonts/MtBkLfRg.ttf
af086000-af914000 r-xp 00000000 08:11 182439     /usr/share/fonts/truetype/kochi/kochi-mincho-subst.ttf
af914000-afa16000 rwxp af914000 00:00 0 
afa16000-afa24000 r-xp 00000000 08:11 423523     /home/mohamed/.Games/SecondLife/fonts/MtBkLfRg.ttf
afa24000-b02b2000 r-xp 00000000 08:11 182439     /usr/share/fonts/truetype/kochi/kochi-mincho-subst.ttf
b02b2000-b03b4000 rwxp b02b2000 00:00 0 
b03b4000-b03c2000 r-xp 00000000 08:11 423523     /home/mohamed/.Games/SecondLife/fonts/MtBkLfRg.ttf
b03c2000-b0c50000 r-xp 00000000 08:11 182439     /usr/share/fonts/truetype/kochi/kochi-mincho-subst.ttf
b0c50000-b0c5e000 r-xp 00000000 08:11 423525     /home/mohamed/.Games/SecondLife/fonts/profontwindows.ttf
b0c5e000-b0c9f000 rwxp b0c5e000 00:00 0 
b0c9f000-b0ca0000 rwxs 00000000 00:08 12550163   /SYSV00000000 (deleted)
b0ca0000-b0ca1000 rwxs 00000000 00:08 10289184   /SYSV00000000 (deleted)
b0ca1000-b0ce1000 rwxs df1c8000 00:0d 17241      /dev/nvidia0
b0ce1000-b0de1000 rwxs e0e1e000 00:0d 17241      /dev/nvidia0
b0de1000-b0ee3000 rwxs e0d1b000 00:0d 17241      /dev/nvidia0
b0ee3000-b0ee4000 rwxs 00000000 00:08 5570627    /SYSV00000000 (deleted)
b0ee4000-b0f25000 rwxp b0ee4000 00:00 0 
b0f25000-b0f8a000 rwxp 00000000 00:0d 2606       /dev/zero
b0f8b000-b128b000 rwxs d0000000 00:0d 17241      /dev/nvidia0
b128b000-b12ac000 rwxp b128b000 00:00 0 
b12ac000-b12d2000 rwxs 00000000 00:08 0          /SYSV00000000 (deleted)
b12d2000-b12d6000 rwxp b12d2000 00:00 0 
b12d6000-b1336000 rwxs 00000000 00:08 12517394   /SYSV00000000 (deleted)
b1336000-b13ac000 r-xp 00000000 08:11 182525     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b13ac000-b13bb000 r-xp 00000000 08:11 130342     /lib/libbz2.so.1.0.3
b13bb000-b13bc000 rwxp 0000f000 08:11 130342     /lib/libbz2.so.1.0.3
b13bc000-b14d3000 r-xp 00000000 08:11 506951     /usr/lib/libxml2.so.2.6.27
b14d3000-b14d9000 rwxp 00116000 08:11 506951     /usr/lib/libxml2.so.2.6.27
b14d9000-b1509000 r-xp 00000000 08:11 506322     /usr/lib/libcroco-0.6.so.3.0.1
b1509000-b150c000 rwxp 0002f000 08:11 506322     /usr/lib/libcroco-0.6.so.3.0.1
b150c000-b1538000 r-xp 00000000 08:11 506573     /usr/lib/libgsf-1.so.114.0.3
b1538000-b153b000 rwxp 0002b000 08:11 506573     /usr/lib/libgsf-1.so.114.0.3
b153b000-b153c000 rwxp b153b000 00:00 0 
b153c000-b156b000 r-xp 00000000 08:11 506843     /usr/lib/librsvg-2.so.2.16.0
b156b000-b156c000 rwxp 0002f000 08:11 506843     /usr/lib/librsvg-2.so.2.16.0
b156d000-b156f000 r-xp 00000000 08:11 506854     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b156f000-b1570000 rwxp 00001000 08:11 506854     /usr/lib/libscim-x11utils-1.0.so.8.1.0
b1570000-b1571000 rwxs 1b513000 00:0d 17241      /dev/nvidia0
b1571000-b1572000 rwxs df9b8000 00:0d 17241      /dev/nvidia0
b1572000-b1576000 rwxs 1a756000 00:0d 17241      /dev/nvidia0
b1576000-b1577000 rwxs df9ba000 00:0d 17241      /dev/nvidia0
b1577000-b1578000 rwxs 27866000 00:0d 17241      /dev/nvidia0
b1578000-b1579000 rwxs 27865000 00:0d 17241      /dev/nvidia0
b1579000-b157a000 rwxs e4001000 00:0d 17241      /dev/nvidia0
b157a000-b157b000 rwxs e4c05000 00:0d 17241      /dev/nvidia0
b157b000-b157c000 r-xp 00000000 08:11 48940      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b157c000-b157d000 rwxp 00001000 08:11 48940      /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b157d000-b1590000 r-xp 00000000 08:11 182592     /usr/share/fonts/truetype/ttf-tamil-fonts/TSCu_Comic.ttf
b1590000-b1592000 r-xp 00000000 08:11 100290     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b1592000-b1593000 rwxp 00001000 08:11 100290     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b1593000-b1599000 r-xs 00000000 08:11 439856     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b1599000-b159a000 r-xs 00000000 08:11 439884     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b159a000-b159d000 r-xs 00000000 08:11 439872     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b159d000-b159e000 r-xs 00000000 08:11 439878     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b159e000-b159f000 r-xs 00000000 08:11 439859     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b159f000-b15a3000 r-xs 00000000 08:11 439853     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b15a3000-b15a4000 r-xs 00000000 08:11 439841     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b15a4000-b15a6000 r-xs 00000000 08:11 439846     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b15a6000-b15a8000 r-xs 00000000 08:11 439834     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b15a8000-b15a9000 r-xs 00000000 08:11 439849     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b15a9000-b15ab000 r-xs 00000000 08:11 439857     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b15ab000-b15b1000 r-xs 00000000 08:11 439847     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b15b1000-b15b3000 r-xs 00000000 08:11 439873     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b15b3000-b15b5000 r-xs 00000000 08:11 439870     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b15b5000-b15bd000 r-xs 00000000 08:11 439876     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b15bd000-b15c3000 r-xs 00000000 08:11 439830     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b15c3000-b15c4000 r-xs 00000000 08:11 439839     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b15c4000-b15db000 r-xs 00000000 08:11 447031     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b15db000-b15dd000 r-xs 00000000 08:11 439874     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b15dd000-b15e3000 r-xs 00000000 08:11 439868     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b15e3000-b15e6000 r-xs 00000000 08:11 439845     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b15e6000-b15ea000 r-xs 00000000 08:11 439828     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b15ea000-b15ec000 r-xs 00000000 08:11 446592     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b15ec000-b15ed000 r-xs 00000000 08:11 439882     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b15ed000-b15ee000 r-xs 00000000 08:11 439879     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b15ee000-b15ef000 r-xs 00000000 08:11 439864     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b15ef000-b15f0000 r-xs 00000000 08:11 439835     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b15f0000-b15f1000 r-xs 00000000 08:11 447138     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b15f1000-b15f4000 r-xs 00000000 08:11 439861     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b15f4000-b15f9000 r-xs 00000000 08:11 447137     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b15f9000-b15fb000 r-xs 00000000 08:11 439827     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b15fb000-b15fc000 r-xs 00000000 08:11 439880     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b15fc000-b15fe000 r-xs 00000000 08:11 439832     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b15fe000-b15ff000 r-xs 00000000 08:11 439858     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b15ff000-b1604000 r-xs 00000000 08:11 439852     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b1604000-b1608000 r-xs 00000000 08:11 439829     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b1608000-b160a000 r-xs 00000000 08:11 439850     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b160a000-b160d000 r-xs 00000000 08:11 439842     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b160d000-b160e000 r-xs 00000000 08:11 439875     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b160e000-b1610000 r-xs 00000000 08:11 439837     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b1610000-b1614000 r-xs 00000000 08:11 447135     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b1614000-b161a000 r-xs 00000000 08:11 439831     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b161a000-b1622000 r-xs 00000000 08:11 439860     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b1622000-b1624000 r-xs 00000000 08:11 447134     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b1624000-b1910000 r-xp 00000000 08:11 130361     /usr/share/icons/hicolor/icon-theme.cache
b1910000-b2b29000 r-xp 00000000 08:11 521618     /usr/share/icons/crystalsvg/icon-theme.cache
b2b29000-b31d0000 r-xp 00000000 08:11 136034     /usr/share/icons/gnome/icon-theme.cache
b31d0000-b3427000 r-xp 00000000 08:11 136024     /usr/share/icons/Tango/icon-theme.cache
b3427000-b34c8000 r-xp 00000000 08:11 136022     /usr/share/icons/Tangerine/icon-theme.cache
b34c8000-b34da000 r-xp 00000000 08:11 48912      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b34da000-b34db000 rwxp 00011000 08:11 48912      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b34db000-b355b000 r-xp 00000000 08:11 456267     /home/mohamed/.Games/SecondLife/lib/libkdu_v42R.so
b355b000-b3562000 rwxp 0007f000 08:11 456267     /home/mohamed/.Games/SecondLife/lib/libkdu_v42R.so
b3562000-b3563000 rwxp b3562000 00:00 0 
b3563000-b3603000 r-xp 00000000 08:11 423529     /home/mohamed/.Games/SecondLife/bin/libllkdu.so
b3603000-b3612000 rwxp 000a0000 08:11 423529     /home/mohamed/.Games/SecondLife/bin/libllkdu.so
b3612000-b3618000 rwxp b3612000 00:00 0 
b3618000-b3619000 ---p b3618000 00:00 0 
b3619000-b3e19000 rwxp b3619000 00:00 0 
b3e19000-b3e1a000 ---p b3e19000 00:00 0 
b3e1a000-b461a000 rwxp b3e1a000 00:00 0 
b461a000-b461b000 ---p b461a000 00:00 0 
b461b000-b4e1b000 rwxp b461b000 00:00 0 
b4e1b000-b4e1c000 ---p b4e1b000 00:00 0 
b4e1c000-b561c000 rwxp b4e1c000 00:00 0 
b561c000-b5625000 r-xp 00000000 08:11 163872     /lib/tls/i686/cmov/libnss_files-2.5.so
b5625000-b5627000 rwxp 00008000 08:11 163872     /lib/tls/i686/cmov/libnss_files-2.5.so
b5627000-b562f000 r-xp 00000000 08:11 163876     /lib/tls/i686/cmov/libnss_nis-2.5.so
b562f000-b5631000 rwxp 00007000 08:11 163876     /lib/tls/i686/cmov/libnss_nis-2.5.so
b5631000-b5644000 r-xp 00000000 08:11 163866     /lib/tls/i686/cmov/libnsl-2.5.so
b5644000-b5646000 rwxp 00012000 08:11 163866     /lib/tls/i686/cmov/libnsl-2.5.so
b5646000-b5648000 rwxp b5646000 00:00 0 
b5648000-b564b000 r-xs 00000000 08:11 439862     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b564b000-b564d000 r-xs 00000000 08:11 447132     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b564d000-b564e000 r-xp 00000000 08:11 33775      /usr/lib/gconv/ISO8859-1.so
b564e000-b5650000 rwxp 00000000 08:11 33775      /usr/lib/gconv/ISO8859-1.so
b5650000-b5657000 r-xs 00000000 08:11 33828      /usr/lib/gconv/gconv-modules.cache
b5657000-b56bd000 rwxp b5657000 00:00 0 
b56bd000-b56d2000 r-xp 00000000 08:11 506174     /usr/lib/libICE.so.6.3.0
b56d2000-b56d4000 rwxp 00014000 08:11 506174     /usr/lib/libICE.so.6.3.0
b56d4000-b56d5000 rwxp b56d4000 00:00 0 
b56d5000-b56dd000 r-xp 00000000 08:11 506192     /usr/lib/libSM.so.6.0.0
b56dd000-b56de000 rwxp 00007000 08:11 506192     /usr/lib/libSM.so.6.0.0
b56de000-b56df000 rwxp b56de000 00:00 0 
b56df000-b5701000 r-xp 00000000 08:11 506811     /usr/lib/libpng12.so.0.15.0
b5701000-b5702000 rwxp 00021000 08:11 506811     /usr/lib/libpng12.so.0.15.0
b5702000-b576a000 r-xp 00000000 08:11 506414     /usr/lib/libfreetype.so.6.3.10
b576a000-b576d000 rwxp 00068000 08:11 506414     /usr/lib/libfreetype.so.6.3.10
b576d000-b5797000 r-xp 00000000 08:11 506790     /usr/lib/libpangoft2-1.0.so.0.1600.2
b5797000-b5798000 rwxp 0002a000 08:11 506790     /usr/lib/libpangoft2-1.0.so.0.1600.2
b5798000-b579c000 r-xp 00000000 08:11 506213     /usr/lib/libXdmcp.so.6.0.0
b579c000-b579d000 rwxp 00003000 08:11 506213     /usr/lib/libXdmcp.so.6.0.0
b579d000-b579e000 rwxp b579d000 00:00 0 
b579e000-b57a0000 r-xp 00000000 08:11 506202     /usr/lib/libXau.so.6.0.0
b57a0000-b57a1000 rwxp 00001000 08:11 506202     /usr/lib/libXau.so.6.0.0
b57a1000-b57a9000 r-xp 00000000 08:11 506209     /usr/lib/libXcursor.so.1.0.2
b57a9000-b57aa000 rwxp 00007000 08:11 506209     /usr/lib/libXcursor.so.1.0.2
b57aa000-b57af000 r-xp 00000000 08:11 506237     /usr/lib/libXrandr.so.2.1.0
b57af000-b57b0000 rwxp 00005000 08:11 506237     /usr/lib/libXrandr.so.2.1.0
b57b0000-b57b7000 r-xp 00000000 08:11 506225     /usr/lib/libXi.so.6.0.0
b57b7000-b57b8000 rwxp 00006000 08:11 506225     /usr/lib/libXi.so.6.0.0
b57b8000-b57ba000 r-xp 00000000 08:11 506227     /usr/lib/libXinerama.so.1.0.0
b57ba000-b57bb000 rwxp 00001000 08:11 506227     /usr/lib/libXinerama.so.1.0.0
b57bb000-b57bc000 rwxp b57bb000 00:00 0 
b57bc000-b57c3000 r-xp 00000000 08:11 506239     /usr/lib/libXrender.so.1.3.0
b57c3000-b57c4000 rwxp 00006000 08:11 506239     /usr/lib/libXrender.so.1.3.0
b57c4000-b57e7000 r-xp 00000000 08:11 506404     /usr/lib/libfontconfig.so.1.2.0
b57e7000-b57ef000 rwxp 00023000 08:11 506404     /usr/lib/libfontconfig.so.1.2.0
b57ef000-b57fc000 r-xp 00000000 08:11 506217     /usr/lib/libXext.so.6.4.0
b57fc000-b57fd000 rwxp 0000d000 08:11 506217     /usr/lib/libXext.so.6.4.0
b57fd000-b57fe000 r-xp 00000000 08:11 374692     /usr/lib/tls/libnvidia-tls.so.1.0.9631
b57fe000-b57ff000 rwxp 00000000 08:11 374692     /usr/lib/tls/libnvidia-tls.so.1.0.9631
b57ff000-b604c000 r-xp 00000000 08:11 515189     /usr/lib/libGLcore.so.1.0.9631
b604c000-b6081000 rwxp 0084d000 08:11 515189     /usr/lib/libGLcore.so.1.0.9631
b6081000-b6086000 rwxp b6081000 00:00 0 
b6086000-b6088000 r-xp 00000000 08:11 488715     /home/mohamed/.Games/SecondLife/lib/libuuid.so.1
b6088000-b6089000 rwxp 00001000 08:11 488715     /home/mohamed/.Games/SecondLife/lib/libuuid.so.1
b6089000-b608e000 r-xp 00000000 08:11 163859     /lib/tls/i686/cmov/libcrypt-2.5.so
b608e000-b6090000 rwxp 00004000 08:11 163859     /lib/tls/i686/cmov/libcrypt-2.5.so
b6090000-b60b7000 rwxp b6090000 00:00 0 
b60b7000-b60be000 r-xp 00000000 08:11 163885     /lib/tls/i686/cmov/librt-2.5.so
b60be000-b60c0000 rwxp 00006000 08:11 163885     /lib/tls/i686/cmov/librt-2.5.so
b60c0000-b610d000 r-xp 00000000 08:11 506243     /usr/lib/libXt.so.6.0.0
b610d000-b6111000 rwxp 0004c000 08:11 506243     /usr/lib/libXt.so.6.0.0
b6111000-b6112000 rwxp b6111000 00:00 0 
b6112000-b611c000 r-xp 00000000 08:11 506794     /usr/lib/libpangox-1.0.so.0.1600.2
b611c000-b611d000 rwxp 00009000 08:11 506794     /usr/lib/libpangox-1.0.so.0.1600.2
b611d000-b6123000 r-xp 00000000 08:11 506796     /usr/lib/libpangoxft-1.0.so.0.1600.2
b6123000-b6124000 rwxp 00005000 08:11 506796     /usr/lib/libpangoxft-1.0.so.0.1600.2
b6124000-b6135000 r-xp 00000000 08:11 506223     /usr/lib/libXft.so.2.1.2
b6135000-b6136000 rwxp 00010000 08:11 506223     /usr/lib/libXft.so.2.1.2
b6136000-b61a4000 r-xp 00000000 08:11 506306     /usr/lib/libcairo.so.2.11.1
b61a4000-b61a6000 rwxp 0006d000 08:11 506306     /usr/lib/libcairo.so.2.11.1
b61a6000-b61a8000 r-xp 00000000 08:11 163861     /lib/tls/i686/cmov/libdl-2.5.so
b61a8000-b61aa000 rwxp 00001000 08:11 163861     /lib/tls/i686/cmov/libdl-2.5.so
b61aa000-b61ab000 rwxp b61aa000 00:00 0 
b61ab000-b61ad000 r-xp 00000000 08:11 506509     /usr/lib/libgmodule-2.0.so.0.1200.11
b61ad000-b61ae000 rwxp 00002000 08:11 506509     /usr/lib/libgmodule-2.0.so.0.1200.11
b61ae000-b61c7000 r-xp 00000000 08:11 506273     /usr/lib/libatk-1.0.so.0.1809.1
b61c7000-b61c9000 rwxp 00018000 08:11 506273     /usr/lib/libatk-1.0.so.0.1809.1
b61c9000-b61cd000 r-xp 00000000 08:11 506219     /usr/lib/libXfixes.so.3.1.0
b61cd000-b61ce000 rwxp 00003000 08:11 506219     /usr/lib/libXfixes.so.3.1.0
b61ce000-b620a000 r-xp 00000000 08:11 506786     /usr/lib/libpango-1.0.so.0.1600.2
b620a000-b620c000 rwxp 0003b000 08:11 506786     /usr/lib/libpango-1.0.so.0.1600.2
b620c000-b6213000 r-xp 00000000 08:11 506788     /usr/lib/libpangocairo-1.0.so.0.1600.2
b6213000-b6214000 rwxp 00007000 08:11 506788     /usr/lib/libpangocairo-1.0.so.0.1600.2
b6214000-b622a000 r-xp 00000000 08:11 506463     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b622a000-b622b000 rwxp 00015000 08:11 506463     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b622b000-b622c000 rwxp b622b000 00:00 0 
b622c000-b623f000 r-xp 00000000 08:11 163881     /lib/tls/i686/cmov/libpthread-2.5.so
b623f000-b6241000 rwxp 00013000 08:11 163881     /lib/tls/i686/cmov/libpthread-2.5.so
b6241000-b6243000 rwxp b6241000 00:00 0 
b6243000-b62d7000 r-xp 00000000 08:11 506499     /usr/lib/libglib-2.0.so.0.1200.11
b62d7000-b62d8000 rwxp 00093000 08:11 506499     /usr/lib/libglib-2.0.so.0.1200.11
b62d8000-b6311000 r-xp 00000000 08:11 506553     /usr/lib/libgobject-2.0.so.0.1200.11
b6311000-b6312000 rwxp 00039000 08:11 506553     /usr/lib/libgobject-2.0.so.0.1200.11
b6312000-b63ff000 r-xp 00000000 08:11 506196     /usr/lib/libX11.so.6.2.0
b63ff000-b6403000 rwxp 000ed000 08:11 506196     /usr/lib/libX11.so.6.2.0
b6403000-b6486000 r-xp 00000000 08:11 506461     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b6486000-b6489000 rwxp 00083000 08:11 506461     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b6489000-b65c4000 r-xp 00000000 08:11 163855     /lib/tls/i686/cmov/libc-2.5.so
b65c4000-b65c5000 r-xp 0013b000 08:11 163855     /lib/tls/i686/cmov/libc-2.5.so
b65c5000-b65c7000 rwxp 0013c000 08:11 163855     /lib/tls/i686/cmov/libc-2.5.so
b65c7000-b65cb000 rwxp b65c7000 00:00 0 
b65cb000-b65d6000 r-xp 00000000 08:11 130368     /lib/libgcc_s.so.1
b65d6000-b65d7000 rwxp 0000a000 08:11 130368     /lib/libgcc_s.so.1
b65d7000-b65fc000 r-xp 00000000 08:11 163863     /lib/tls/i686/cmov/libm-2.5.so
b65fc000-b65fe000 rwxp 00024000 08:11 163863     /lib/tls/i686/cmov/libm-2.5.so
b65fe000-b66c9000 r-xp 00000000 08:11 488713     /home/mohamed/.Games/SecondLife/lib/libstdc++.so.6
b66c9000-b66ce000 rwxp 000cb000 08:11 488713     /home/mohamed/.Games/SecondLife/lib/libstdc++.so.6
b66ce000-b66d3000 rwxp b66ce000 00:00 0 
b66d3000-b6731000 r-xp 00000000 08:11 488694     /home/mohamed/.Games/SecondLife/lib/libfmod-3.75.so
b6731000-b6740000 rwxp 0005d000 08:11 488694     /home/mohamed/.Games/SecondLife/lib/libfmod-3.75.so
b6740000-b676e000 rwxp b6740000 00:00 0 
b676e000-b6842000 r-xp 00000000 08:11 488704     /home/mohamed/.Games/SecondLife/lib/libdb-4.2.so
b6842000-b6844000 rwxp 000d4000 08:11 488704     /home/mohamed/.Games/SecondLife/lib/libdb-4.2.so
b6844000-b6845000 rwxp b6844000 00:00 0 
b6845000-b6861000 r-xp 00000000 08:11 488706     /home/mohamed/.Games/SecondLife/lib/libvorbis.so.0
b6861000-b6864000 rwxp 0001b000 08:11 488706     /home/mohamed/.Games/SecondLife/lib/libvorbis.so.0
b6864000-b6869000 r-xp 00000000 08:11 488707     /home/mohamed/.Games/SecondLife/lib/libvorbisfile.so.0
b6869000-b686a000 rwxp 00004000 08:11 488707     /home/mohamed/.Games/SecondLife/lib/libvorbisfile.so.0
b686a000-b6874000 r-xp 00000000 08:11 488708     /home/mohamed/.Games/SecondLife/lib/libvorbisenc.so.0
b6874000-b68e2000 rwxp 0000a000 08:11 488708     /home/mohamed/.Games/SecondLife/lib/libvorbisenc.so.0
b68e2000-b68e5000 r-xp 00000000 08:11 488705     /home/mohamed/.Games/SecondLife/lib/libogg.so.0
b68e5000-b68e6000 rwxp 00002000 08:11 488705     /home/mohamed/.Games/SecondLife/lib/libogg.so.0
b68e6000-b6965000 r-xp 00000000 08:11 506169     /usr/lib/libGLU.so.1.3.060502
b6965000-b6966000 rwxp 0007e000 08:11 506169     /usr/lib/libGLU.so.1.3.060502
b6966000-b6967000 rwxp b6966000 00:00 0 
b6967000-b69d8000 r-xp 00000000 08:11 515188     /usr/lib/libGL.so.1.0.9631
b69d8000-b69f2000 rwxp 00070000 08:11 515188     /usr/lib/libGL.so.1.0.9631
b69f2000-b69f3000 rwxp b69f2000 00:00 0 
b69f3000-b6a59000 r-xp 00000000 08:11 488716     /home/mohamed/.Games/SecondLife/lib/libSDL-1.2.so.0
b6a59000-b6a5b000 rwxp 00066000 08:11 488716     /home/mohamed/.Games/SecondLife/lib/libSDL-1.2.so.0
b6a5b000-b6a74000 rwxp b6a5b000 00:00 0 
b6a74000-b6a87000 r-xp 00000000 08:11 506957     /usr/lib/libz.so.1.2.3
b6a87000-b6a88000 rwxp 00012000 08:11 506957     /usr/lib/libz.so.1.2.3
b6a88000-b6aaa000 r-xp 00000000 08:11 488702     /home/mohamed/.Games/SecondLife/lib/libapr-1.so.0
b6aaa000-b6aab000 rwxp 00021000 08:11 488702     /home/mohamed/.Games/SecondLife/lib/libapr-1.so.0
b6aab000-b6abf000 r-xp 00000000 08:11 488703     /home/mohamed/.Games/SecondLife/lib/libaprutil-1.so.0
b6abf000-b6ac0000 rwxp 00014000 08:11 488703     /home/mohamed/.Games/SecondLife/lib/libaprutil-1.so.0
b6ac0000-b6ac1000 rwxp b6ac0000 00:00 0 
b6ac1000-b6ade000 r-xp 00000000 08:11 488712     /home/mohamed/.Games/SecondLife/lib/libexpat.so.1
b6ade000-b6ae1000 rwxp 0001d000 08:11 488712     /home/mohamed/.Games/SecondLife/lib/libexpat.so.1
b6ae1000-b6bbe000 r-xp 00000000 08:11 488710     /home/mohamed/.Games/SecondLife/lib/libcrypto.so.0.9.7
b6bbe000-b6bd0000 rwxp 000dc000 08:11 488710     /home/mohamed/.Games/SecondLife/lib/libcrypto.so.0.9.7
b6bd0000-b6bd3000 rwxp b6bd0000 00:00 0 
b6bd3000-b6bfe000 r-xp 00000000 08:11 488711     /home/mohamed/.Games/SecondLife/lib/libssl.so.0.9.7
b6bfe000-b6c01000 rwxp 0002b000 08:11 488711     /home/mohamed/.Games/SecondLife/lib/libssl.so.0.9.7
b6c01000-b6c32000 r-xp 00000000 08:11 488709     /home/mohamed/.Games/SecondLife/lib/libcurl.so.4
b6c32000-b6c33000 rwxp 00031000 08:11 488709     /home/mohamed/.Games/SecondLife/lib/libcurl.so.4
b6c33000-b7ab5000 r-xp 00000000 08:11 236141     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxul.so
b7ab5000-b7b59000 rwxp 00e81000 08:11 236141     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxul.so
b7b59000-b7b6c000 rwxp b7b59000 00:00 0 
b7b6c000-b7b6e000 r-xp 00000000 08:11 407242     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxpcom.so
b7b6e000-b7b6f000 rwxp 00002000 08:11 407242     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libxpcom.so
b7b6f000-b7b71000 r-xp 00000000 08:11 407243     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libplds4.so
b7b71000-b7b72000 rwxp 00001000 08:11 407243     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libplds4.so
b7b72000-b7b76000 r-xp 00000000 08:11 407247     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libplc4.so
b7b76000-b7b77000 rwxp 00003000 08:11 407247     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libplc4.so
b7b77000-b7ba7000 r-xp 00000000 08:11 407250     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libnspr4.so
b7ba7000-b7ba9000 rwxp 0002f000 08:11 407250     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libnspr4.so
b7ba9000-b7bab000 rwxp b7ba9000 00:00 0 
b7bab000-b7c4a000 r-xp 00000000 08:11 407248     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libmozjs.so
b7c4a000-b7c4f000 rwxp 0009e000 08:11 407248     /home/mohamed/.Games/SecondLife/app_settings/mozilla-runtime-linux-i686/libmozjs.so
b7c4f000-b7c50000 rwxp b7c4f000 00:00 0 
b7c50000-b7c67000 r-xp 00000000 08:11 488714     /home/mohamed/.Games/SecondLife/lib/libelfio.so
b7c67000-b7c68000 rwxp 00016000 08:11 488714     /home/mohamed/.Games/SecondLife/lib/libelfio.so
b7c68000-b7fb9000 r-xp 00000000 08:11 506610     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7fb9000-b7fbf000 rwxp 00351000 08:11 506610     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7fbf000-b7fc0000 rwxp b7fbf000 00:00 0 
b7fc0000-b7fc1000 r-xs 00000000 08:11 439854     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7fc1000-b7fc3000 r-xs 00000000 08:11 446588     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b7fc3000-b7fc4000 rwxp b7fc3000 00:00 0 
b7fc4000-b7fcb000 r-xp 00000000 08:11 163868     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7fcb000-b7fcd000 rwxp 00006000 08:11 163868     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7fcd000-b7fcf000 rwxp 00000000 00:0d 2606       /dev/zero
b7fcf000-b7fd1000 rwxp b7fcf000 00:00 0 
b7fd1000-b7fea000 r-xp 00000000 08:11 130325     /lib/ld-2.5.so
b7fea000-b7fec000 rwxp 00019000 08:11 130325     /lib/ld-2.5.so
bfdcd000-bfdec000 rwxp bfdcd000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]


I turned beryl off
Thanks for your help

---

### Post by sharperguy on 2007-05-29
Your secondlife problem may be caused by scim?

Try disabling it  if you have enabled it


If not, I do't know

---

### Post by Toxicity999 on 2007-05-29
"bin/do-not-directly-run- secondlife-bin"

Is repeated a LOT through your output, are you sure you're starting it properly? It might have some kind of wrapper script you need to run. Did it create a Menu entry, do you see a script which looks like it might be something you want to start instead?

---

### Post by sharperguy on 2007-05-31
Yes I can confirm now that I had this problem and removing scim fixed it.

I had been examining  the output and it didnt show any sign if error and looked exactly like that (which is how it looks when it works)

---

### Post by brodiepearce on 2007-07-20
I've started getting this issue after upgrading to the 1.18.0.6 Alpha (latest one, forced upgrade etc.).  Anyone know of a workaround so that SCIM doesn't need to be disabled?

*edit*
Looks like it's already been noted in the [Second Life bug reports](https://jira.secondlife.com/browse/VWR-738), apparently it's been an issue since 1.16.0.6?  o.O

*edit*
Looks like there _is_ a fix for it that I'd overlooked in the bug report:

Running second life with GTK_IM_MODULE=gtk-im-context-simple will supposedly workaround the issue, but I suppose this will prohibit SCIM input being used in SL.

---

