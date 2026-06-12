---
title: "Pidgin crashes upon opening"
date: 2009-05-17
forum: General Help
---

### Post by Famicommander on 2009-05-17
I just did a fresh install of Jaunty, and pretty much everything works great. But I get this when I open Pidgin:
```
jason@ubuntu:~$ pidgin
*** stack smashing detected ***: pidgin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7719da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7719d60]
/usr/lib/purple-2/libxfire.so[0xb5e408f4]
/usr/lib/purple-2/libxfire.so(gfire_packet_131+0x55b)[0xb5e3ca2c]
/usr/lib/purple-2/libxfire.so(gfire_parse_packet+0x25d)[0xb5e3adbb]
/usr/lib/purple-2/libxfire.so(gfire_input_cb+0x474)[0xb5e3ab56]
pidgin[0x80a8e93]
/usr/lib/libglib-2.0.so.0[0xb78e6dad]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb78afb88]
/usr/lib/libglib-2.0.so.0[0xb78b30eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb78b35ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7ba27d9]
pidgin(main+0x89a)[0x80c31ea]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7632775]
pidgin[0x806db61]
======= Memory map: ========
08048000-0810e000 r-xp 00000000 07:00 211772     /usr/bin/pidgin
0810e000-0810f000 r--p 000c5000 07:00 211772     /usr/bin/pidgin
0810f000-08112000 rw-p 000c6000 07:00 211772     /usr/bin/pidgin
085b6000-08f61000 rw-p 085b6000 00:00 0          [heap]
b570e000-b576e000 rw-s 00000000 00:09 2490381    /SYSV00000000 (deleted)
b576e000-b57ce000 rw-s 00000000 00:09 2457612    /SYSV00000000 (deleted)
b57ce000-b585a000 r--p 00000000 07:00 348997     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b585a000-b585b000 r-xp 00000000 07:00 413899     /usr/lib/gconv/ISO8859-1.so
b585b000-b585c000 r--p 00001000 07:00 413899     /usr/lib/gconv/ISO8859-1.so
b585c000-b585d000 rw-p 00002000 07:00 413899     /usr/lib/gconv/ISO8859-1.so
b585d000-b592c000 rw-p b585d000 00:00 0 
b592c000-b596b000 r-xp 00000000 07:00 213044     /usr/lib/libhunspell-1.2.so.0.0.0
b596b000-b596c000 r--p 0003e000 07:00 213044     /usr/lib/libhunspell-1.2.so.0.0.0
b596c000-b5970000 rw-p 0003f000 07:00 213044     /usr/lib/libhunspell-1.2.so.0.0.0
b597f000-b5a13000 r-xp 00000000 07:00 212572     /usr/lib/libaspell.so.15.1.4
b5a13000-b5a16000 r--p 00093000 07:00 212572     /usr/lib/libaspell.so.15.1.4
b5a16000-b5a17000 rw-p 00096000 07:00 212572     /usr/lib/libaspell.so.15.1.4
b5a17000-b5a1b000 rw-p b5a17000 00:00 0 
b5a24000-b5a28000 r-xp 00000000 07:00 283924     /usr/lib/enchant/libenchant_myspell.so
b5a28000-b5a29000 r--p 00003000 07:00 283924     /usr/lib/enchant/libenchant_myspell.so
b5a29000-b5a2a000 rw-p 00004000 07:00 283924     /usr/lib/enchant/libenchant_myspell.so
b5a2a000-b5a2c000 r-xp 00000000 07:00 283921     /usr/lib/enchant/libenchant_aspell.so
b5a2c000-b5a2d000 r--p 00001000 07:00 283921     /usr/lib/enchant/libenchant_aspell.so
b5a2d000-b5a2e000 rw-p 00002000 07:00 283921     /usr/lib/enchant/libenchant_aspell.so
b5a2e000-b5a36000 r-xp 00000000 07:00 283922     /usr/lib/enchant/libenchant_hspell.so
b5a36000-b5a37000 r--p 00007000 07:00 283922     /usr/lib/enchant/libenchant_hspell.so
b5a37000-b5a39000 rw-p 00008000 07:00 283922     /usr/lib/enchant/libenchant_hspell.so
b5a39000-b5a46000 r-xp 00000000 07:00 64961      /lib/libgcc_s.so.1
b5a46000-b5a47000 r--p 0000c000 07:00 64961      /lib/libgcc_s.so.1
b5a47000-b5a48000 rw-p 0000d000 07:00 64961      /lib/libgcc_s.so.1
b5a48000-b5b2c000 r-xp 00000000 07:00 213381     /usr/lib/libstdc++.so.6.0.10
b5b2c000-b5b30000 r--p 000e3000 07:00 213381     /usr/lib/libstdc++.so.6.0.10
b5b30000-b5b31000 rw-p 000e7000 07:00 213381     /usr/lib/libstdc++.so.6.0.10
b5b31000-b5b37000 rw-p b5b31000 00:00 0 
b5b39000-b5b44000 r-xp 00000000 07:00 283923     /usr/lib/enchant/libenchant_ispell.so
b5b44000-b5b45000 r--p 0000a000 07:00 283923     /usr/lib/enchant/libenchant_ispell.so
b5b45000-b5b46000 rw-p 0000b000 07:00 283923     /usr/lib/enchant/libenchant_ispell.so
b5b46000-b5b48000 r-xp 00000000 07:00 283925     /usr/lib/enchant/libenchant_zemberek.so
b5b48000-b5b49000 r--p 00001000 07:00 283925     /usr/lib/enchant/libenchant_zemberek.so
b5b49000-b5b4a000 rw-p 00002000 07:00 283925     /usr/lib/enchant/libenchant_zemberek.so
b5b4a000-b5b4c000 r-xp 00000000 07:00 236500     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5b4c000-b5b4d000 r--p 00001000 07:00 236500     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5b4d000-b5b4e000 rw-p 00002000 07:00 236500     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5b4e000-b5be6000 r--p 00000000 07:00 348998     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5be6000-b5bec000 r--s 00000000 07:00 246766     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5bec000-b5bef000 r--s 00000000 07:00 246775     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5bef000-b5bf3000 r--s 00000000 07:00 244284     /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b5bf3000-b5bf6000 r--s 00000000 07:00 244280     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b5bf6000-b5bf7000 r--s 00000000 07:00 246761     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5bf7000-b5bfa000 r--s 00000000 07:00 246767     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5bfa000-b5c01000 r--s 00000000 07:00 244300     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5c01000-b5c04000 r--s 00000000 07:00 246773     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5c04000-b5c0c000 r--s 00000000 07:00 246776     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5c0c000-b5c17000 r--s 00000000 07:00 246756     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5c17000-b5c39000 r--s 00000000 07:00 243739     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5c39000-b5c40000 r--s 00000000 07:00 246770     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5c40000-b5c58000 r--s 00000000 07:00 262635     /usr/share/mime/mime.cache
b5c58000-b5c67000 r-xp 00000000 07:00 236484     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5c67000-b5c68000 r--p 0000e000 07:00 236484     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5c68000-b5c69000 rw-p 0000f000 07:00 236484     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5c69000-b5c7b000 r-xp 00000000 07:00 213031     /usr/lib/libgvfscommon.so.0.0.0
b5c7b000-b5c7c000 r--p 00012000 07:00 213031     /usr/lib/libgvfscommon.so.0.0.0
b5c7c000-b5c7d000 rw-p 00013000 07:00 213031     /usr/lib/libgvfscommon.so.0.0.0
b5c7d000-b5c97000 r-xp 00000000 07:00 236485     /usr/lib/gio/modules/libgvfsdbus.so
b5c97000-b5c98000 r--p 00019000 07:00 236485     /usr/lib/gio/modules/libgvfsdbus.so
b5c98000-b5c99000 rw-p 0001a000 07:00 236485     /usr/lib/gio/modules/libgvfsdbus.so
b5c99000-b5cdf000 r-xp 00000000 07:00 324625     /usr/lib/nss/libnssckbi.so
b5cdf000-b5ce7000 r--p 00045000 07:00 324625     /usr/lib/nss/libnssckbi.so
b5ce7000-b5ceb000 rw-p 0004d000 07:00 324625     /usr/lib/nss/libnssckbi.so
b5ceb000-b5d2f000 r-xp 00000000 07:00 324624     /usr/lib/nss/libfreebl3.so
b5d2f000-b5d30000 r--p 00043000 07:00 324624     /usr/lib/nss/libfreebl3.so
b5d30000-b5d31000 rw-p 00044000 07:00 324624     /usr/lib/nss/libfreebl3.so
b5d31000-b5d65000 r-xp 00000000 07:00 324628     /usr/lib/nss/libsoftokn3.so
b5d65000-b5d66000 r--p 00034000 07:00 324628     /usr/lib/nss/libsoftokn3.so
b5d66000-b5d67000 rw-p 00035000 07:00 324628     /usr/lib/nss/libsoftokn3.so
b5d67000-b5d96000 r-xp 00000000 07:00 64976      /lib/libncurses.so.5.7
b5d96000-b5d98000 r--p 0002e000 07:00 64976      /lib/libncurses.so.5.7
b5d98000-b5d99000 rw-p 00030000 07:00 64976      /lib/libncurses.so.5.7
b5d99000-b5dc5000 r-xp 00000000 07:00 65020      /lib/libreadline.so.5.2
b5dc5000-b5dc6000 ---p 0002c000 07:00 65020      /lib/libreadline.so.5.2
b5dc6000-b5dc7000 r--p 0002c000 07:00 65020      /lib/libreadline.so.5.2
b5dc7000-b5dca000 rw-p 0002d000 07:00 65020      /lib/libreadline.so.5.2
b5dca000-b5dcb000 rw-p b5dca000 00:00 0 
b5dcb000-b5dd4000 r-xp 00000000 07:00 213474     /usr/lib/libzephyr.so.3.0.0
b5dd4000-b5dd5000 ---p 00009000 07:00 213474     /usr/lib/libzephyr.so.3.0.0
b5dd5000-b5dd6000 r--p 00009000 07:00 213474     /usr/lib/libzephyr.so.3.0.0
b5dd6000-b5dd7000 rw-p 0000a000 07:00 213474     /usr/lib/libzephyr.so.3.0.0
b5dd7000-b5dda000 rw-p b5dd7000 00:00 0 
b5ddc000-b5de2000 r--s 00000000 07:00 246755     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5de2000-b5de9000 r--s 00000000 07:00 244281     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5de9000-b5df5000 r-xp 00000000 07:00 494859     /usr/lib/purple-2/libzephyr.so
b5df5000-b5df6000 r--p 0000b000 07:00 494859     /usr/lib/purple-2/libzephyr.so
b5df6000-b5df7000 rw-p 0000c000 07:00 494859     /usr/lib/purple-2/libzephyr.so
b5df7000-b5e30000 r-xp 00000000 07:00 494858     /usr/lib/purple-2/libyahoo.so
b5e30000-b5e31000 ---p 00039000 07:00 494858     /usr/lib/purple-2/libyahoo.so
b5e31000-b5e32000 r--p 00039000 07:00 494858     /usr/lib/purple-2/libyahoo.so
b5e32000-b5e33000 rw-p 0003a000 07:00 494858     /usr/lib/purple-2/libyahoo.so
b5e33000-b5e43000 r-Aborted
jason@ubuntu:~$ 

```

I have absolutely zero idea what that means. Anyone have any idea? Thanks.

---

### Post by Famicommander on 2009-05-17
Fixed. Turns out I was just using an older version of gfire. All is well.

---

