---
title: "freerdp going fullscreen"
date: 2013-09-26
forum: Desktop Environments
---

### Post by xav!or on 2013-09-26
when I try the /f fullscreen command in lubuntu it fails.  other apps go fullscreen.  I tried changing video card.  didn't work.  I then tried upgrading video drivers.  didn't work.  is it because its using the lightdm desktop manager?

---

### Post by xav!or on 2013-09-26
error i get:

*** glibc detected *** xfreerdp: corrupted double-link list: 0x097cb600 ***

---

### Post by xav!or on 2013-09-26
WaitForSingleObject: unknown handle type 151664112
WaitForSingleObject: unknown handle type 151664112
*** glibc detected *** xfreerdp: corrupted double-linked list: 0x090a3610 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x75ee2)[0xb75d4ee2]
/lib/i386-linux-gnu/libc.so.6(+0x76258)[0xb75d5258]
/lib/i386-linux-gnu/libc.so.6(+0x7722f)[0xb75d622f]
/lib/i386-linux-gnu/libc.so.6(+0x787d7)[0xb75d77d7]
/lib/i386-linux-gnu/libc.so.6(realloc+0xe7)[0xb75d93f7]
/usr/lib/i386-linux-gnu/libfreerdp-core.so.1.1(update_read_bitmap+0xaf)[0xb739de1f]
/usr/lib/i386-linux-gnu/libfreerdp-core.so.1.1(+0x39032)[0xb739a032]
/usr/lib/i386-linux-gnu/libfreerdp-core.so.1.1(fastpath_recv_updates+0xf0)[0xb739a2a0]
/usr/lib/i386-linux-gnu/libfreerdp-core.so.1.1(+0x37c18)[0xb7398c18]
/usr/lib/i386-linux-gnu/libfreerdp-core.so.1.1(transport_check_fds+0xbb)[0xb739c65b]
/usr/lib/i386-linux-gnu/libfreerdp-core.so.1.1(rdp_check_fds+0x1e)[0xb73990fe]
/usr/lib/i386-linux-gnu/libfreerdp-core.so.1.1(freerdp_check_fds+0x23)[0xb738bf83]
/usr/lib/i386-linux-gnu/libxfreerdp-client.so.1.1(xf_thread+0x503)[0xb7727363]
/lib/i386-linux-gnu/libpthread.so.0(+0x6d4c)[0xb72b8d4c]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0xb764ddde]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:01 1193724    /usr/bin/xfreerdp
0804a000-0804b000 r--p 00001000 08:01 1193724    /usr/bin/xfreerdp
0804b000-0804c000 rw-p 00002000 08:01 1193724    /usr/bin/xfreerdp
09084000-090ef000 rw-p 00000000 00:00 0          [heap]
b4d00000-b4d82000 rw-p 00000000 00:00 0 
b4d82000-b4e00000 ---p 00000000 00:00 0 
b4e18000-b4e2b000 r-xp 00000000 08:01 261816     /lib/i386-linux-gnu/libresolv-2.15.so
b4e2b000-b4e2c000 ---p 00013000 08:01 261816     /lib/i386-linux-gnu/libresolv-2.15.so
b4e2c000-b4e2d000 r--p 00013000 08:01 261816     /lib/i386-linux-gnu/libresolv-2.15.so
b4e2d000-b4e2e000 rw-p 00014000 08:01 261816     /lib/i386-linux-gnu/libresolv-2.15.so
b4e2e000-b4e30000 rw-p 00000000 00:00 0 
b4e30000-b4e35000 r-xp 00000000 08:01 261818     /lib/i386-linux-gnu/libnss_dns-2.15.so
b4e35000-b4e36000 r--p 00004000 08:01 261818     /lib/i386-linux-gnu/libnss_dns-2.15.so
b4e36000-b4e37000 rw-p 00005000 08:01 261818     /lib/i386-linux-gnu/libnss_dns-2.15.so
b4e37000-b4e39000 r-xp 00000000 08:01 265830     /lib/libnss_mdns4_minimal.so.2
b4e39000-b4e3a000 r--p 00001000 08:01 265830     /lib/libnss_mdns4_minimal.so.2
b4e3a000-b4e3b000 rw-p 00002000 08:01 265830     /lib/libnss_mdns4_minimal.so.2
b4e3b000-b4e46000 r-xp 00000000 08:01 261814     /lib/i386-linux-gnu/libnss_files-2.15.so
b4e46000-b4e47000 r--p 0000a000 08:01 261814     /lib/i386-linux-gnu/libnss_files-2.15.so
b4e47000-b4e48000 rw-p 0000b000 08:01 261814     /lib/i386-linux-gnu/libnss_files-2.15.so
b4e59000-b4e5a000 ---p 00000000 00:00 0 
b4e5a000-b567b000 rw-p 00000000 00:00 0          [stack:2085]
b567b000-b587b000 r--p 00000000 08:01 1183072    /usr/lib/locale/locale-archive
b587b000-b5880000 rw-p 00000000 00:00 0 
b5880000-b5958000 r-xp 00000000 08:01 1182459    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b5958000-b5959000 ---p 000d8000 08:01 1182459    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b5959000-b595d000 r--p 000d8000 08:01 1182459    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b595d000-b595e000 rw-p 000dc000 08:01 1182459    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b595e000-b5965000 rw-p 00000000 00:00 0 
b5965000-b5981000 r-xp 00000000 08:01 261684     /lib/i386-linux-gnu/libgcc_s.so.1
b5981000-b5982000 r--p 0001b000 08:01 261684     /lib/i386-linux-gnu/libgcc_s.so.1
b5982000-b5983000 rw-p 0001c000 08:01 261684     /lib/i386-linux-gnu/libgcc_s.so.1
b5983000-b5984000 rw-p 00000000 00:00 0 
b5984000-b5a0f000 r-xp 00000000 08:01 1193146    /usr/lib/i386-linux-gnu/liborc-0.4.so.0.16.0
b5a0f000-b5a10000 r--p 0008a000 08:01 1193146    /usr/lib/i386-linux-gnu/liborc-0.4.so.0.16.0
b5a10000-b5a14000 rw-p 0008b000 08:01 1193146    /usr/lib/i386-linux-gnu/liborc-0.4.so.0.16.0
b5a14000-b5a1a000 r-xp 00000000 08:01 1193154    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b5a1a000-b5a1b000 r--p 00005000 08:01 1193154    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b5a1b000-b5a1c000 rw-p 00006000 08:01 1193154    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b5a1c000-b5a6d000 r-xp 00000000 08:01 261681     /lib/i386-linux-gnu/libssl.so.1.0.0
b5a6d000-b5a6f000 r--p 00050000 08:01 261681     /lib/i386-linux-gnu/libssl.so.1.0.0
b5a6f000-b5a73000 rw-p 00052000 08:01 261681     /lib/i386-linux-gnu/libssl.so.1.0.0
b5a73000-b5a7a000 r-xp 00000000 08:01 261819     /lib/i386-linux-gnu/librt-2.15.so
b5a7a000-b5a7b000 r--p 00006000 08:01 261819     /lib/i386-linux-gnu/librt-2.15.so
b5a7b000-b5a7c000 rw-p 00007000 08:01 261819     /lib/i386-linux-gnu/librt-2.15.so
b5a7c000-b5a7d000 rw-p 00000000 00:00 0 
b5a7d000-b5a8d000 r-xp 00000000 08:01 1193163    /usr/lib/i386-linux-gnu/libva.so.1.3200.0
b5a8d000-b5a8e000 r--p 0000f000 08:01 1193163    /usr/lib/i386-linux-gnu/libva.so.1.3200.0
b5a8e000-b5a8f000 rw-p 00010000 08:01 1193163    /usr/lib/i386-linux-gnu/libva.so.1.3200.0
b5a8f000-b5a93000 rw-p 00000000 00:00 0 
b5a93000-b5b17000 r-xp 00000000 08:01 1193138    /usr/lib/libdirac_encoder.so.0.1.0
b5b17000-b5b19000 r--p 00083000 08:01 1193138    /usr/lib/libdirac_encoder.so.0.1.0
b5b19000-b5b1a000 rw-p 00085000 08:01 1193138    /usr/lib/libdirac_encoder.so.0.1.0
b5b1a000-b5b1b000 rw-p 00000000 00:00 0 
b5b1b000-b5b27000 r-xp 00000000 08:01 1193140    /usr/lib/libgsm.so.1.0.12
b5b27000-b5b28000 r--p 0000b000 08:01 1193140    /usr/lib/libgsm.so.1.0.12
b5b28000-b5b29000 rw-p 0000c000 08:01 1193140    /usr/lib/libgsm.so.1.0.12
b5b29000-b5b78000 r-xp 00000000 08:01 1193142    /usr/lib/i386-linux-gnu/libmp3lame.so.0.0.0
b5b78000-b5b79000 ---p 0004f000 08:01 1193142    /usr/lib/i386-linux-gnu/libmp3lame.so.0.0.0
b5b79000-b5b7a000 r--p 0004f000 08:01 1193142    /usr/lib/i386-linux-gnu/libmp3lame.so.0.0.0
b5b7a000-b5b7b000 rw-p 00050000 08:01 1193142    /usr/lib/i386-linux-gnu/libmp3lame.so.0.0.0
b5b7b000-b5bac000 rw-p 00000000 00:00 0 
b5bac000-b5bca000 r-xp 00000000 08:01 1193144    /usr/lib/libopenjpeg-2.1.3.0.so
b5bca000-b5bcb000 r--p 0001d000 08:01 1193144    /usr/lib/libopenjpeg-2.1.3.0.so
b5bcb000-b5bcc000 rw-p 0001e000 08:01 1193144    /usr/lib/libopenjpeg-2.1.3.0.so
b5bcc000-b5bcd000 rw-p 00000000 00:00 0 
b5bcd000-b5be1000 r-xp 00000000 08:01 261862     /lib/i386-linux-gnu/libz.so.1.2.3.4
b5be1000-b5be2000 r--p 00013000 08:01 261862     /lib/i386-linux-gnu/libz.so.1.2.3.4
b5be2000-b5be3000 rw-p 00014000 08:01 261862     /lib/i386-linux-gnu/libz.so.1.2.3.4
b5be3000-b5c9e000 r-xp 00000000 08:01 1193150    /usr/lib/libschroedinger-1.0.so.0.11.0
b5c9e000-b5ca0000 r--p 000ba000 08:01 1193150    /usr/lib/libschroedinger-1.0.so.0.11.0Aborted (core dumped)

---

### Post by xav!or on 2013-09-26
i tried installed gnome-desktop to change the display manager and that didn't work.

---

