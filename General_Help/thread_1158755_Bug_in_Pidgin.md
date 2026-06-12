---
title: "Bug in Pidgin?"
date: 2009-05-14
forum: General Help
---

### Post by m-a on 2009-05-14
I'm having pidgin crashing randomly. I'll put the output on the console at the end of this message.

Now, what's the next step? Do I post a bug to the pidgin mailing list? Or to Ubuntu's maintainers? If the latter, how do I do that?

```

marc-andre@01HW175292:~$ *** glibc detected *** pidgin: double free or corruption (out): 0x08ccdbc0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb769c604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb769e5b6]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb78c9126]
/usr/lib/libglib-2.0.so.0(g_string_free+0x5c)[0xb78e56dc]
/usr/lib/pidgin/nautilus.so[0xb6f6527a]
/usr/lib/libpurple.so.0(purple_marshal_VOID__POINTER+0x18)[0xb781a038]
/usr/lib/libpurple.so.0(purple_signal_emit_vargs+0xb1)[0xb781ab01]
/usr/lib/libpurple.so.0(purple_signal_emit+0x33)[0xb781ac43]
/usr/lib/libpurple.so.0(purple_blist_update_buddy_status+0x116)[0xb77dc0f6]
/usr/lib/libpurple.so.0(purple_prpl_got_user_status+0xc8)[0xb7811ea8]
/usr/lib/purple-2/libsametime.so[0xb54ec851]
/usr/lib/libmeanwhile.so.1[0xb54b4028]
/usr/lib/libmeanwhile.so.1[0xb54b5ed2]
/usr/lib/libmeanwhile.so.1(mwService_recv+0x77)[0xb54b1747]
/usr/lib/libmeanwhile.so.1[0xb54aa7f3]
/usr/lib/libmeanwhile.so.1[0xb54b307f]
/usr/lib/libmeanwhile.so.1(mwSession_recv+0x276)[0xb54b3836]
/usr/lib/purple-2/libsametime.so[0xb54f4414]
/usr/lib/purple-2/libsametime.so[0xb54f446f]
pidgin[0x80a8e93]
/usr/lib/libglib-2.0.so.0[0xb78f7dad]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb78c0b88]
/usr/lib/libglib-2.0.so.0[0xb78c40eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb78c45ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7bb37d9]
pidgin(main+0x89a)[0x80c31ea]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7643775]
pidgin[0x806db61]
======= Memory map: ========
08048000-0810e000 r-xp 00000000 08:08 362076     /usr/bin/pidgin
0810e000-0810f000 r--p 000c5000 08:08 362076     /usr/bin/pidgin
0810f000-08112000 rw-p 000c6000 08:08 362076     /usr/bin/pidgin
08433000-09053000 rw-p 08433000 00:00 0          [heap]
b4200000-b4221000 rw-p b4200000 00:00 0 
b4221000-b4300000 ---p b4221000 00:00 0 
b43f3000-b43f6000 rw-p b43f3000 00:00 0 
b43f6000-b4447000 r--p 00000000 08:08 229750     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-ExtraLight.ttf
b4447000-b44a7000 rw-s 00000000 00:09 4489235    /SYSV00000000 (deleted)
b44a7000-b44b6000 r-xp 00000000 08:08 858208     /lib/libbz2.so.1.0.4
b44b6000-b44b7000 r--p 0000f000 08:08 858208     /lib/libbz2.so.1.0.4
b44b7000-b44b8000 rw-p 00010000 08:08 858208     /lib/libbz2.so.1.0.4
b44b8000-b44e9000 r-xp 00000000 08:08 20923      /usr/lib/libcroco-0.6.so.3.0.1
b44e9000-b44ec000 rw-p 00030000 08:08 20923      /usr/lib/libcroco-0.6.so.3.0.1
b44ec000-b451f000 r-xp 00000000 08:08 17544      /usr/lib/libgsf-1.so.114.0.11
b451f000-b4520000 ---p 00033000 08:08 17544      /usr/lib/libgsf-1.so.114.0.11
b4520000-b4522000 r--p 00033000 08:08 17544      /usr/lib/libgsf-1.so.114.0.11
b4522000-b4523000 rw-p 00035000 08:08 17544      /usr/lib/libgsf-1.so.114.0.11
b4523000-b4524000 rw-p b4523000 00:00 0 
b4524000-b4555000 r-xp 00000000 08:08 385252     /usr/lib/librsvg-2.so.2.26.0
b4555000-b4556000 r--p 00031000 08:08 385252     /usr/lib/librsvg-2.so.2.26.0
b4556000-b4557000 rw-p 00032000 08:08 385252     /usr/lib/librsvg-2.so.2.26.0
b456f000-b45cf000 rw-s 00000000 00:09 4456466    /SYSV00000000 (deleted)
b45cf000-b465b000 r--p 00000000 08:08 229065     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b465b000-b4672000 r--s 00000000 08:08 613517     /var/lib/aspell/en_GB-ise-wo_accents-only.rws
b4672000-b4689000 r--s 00000000 08:08 613521     /var/lib/aspell/en_US-wo_accents-only.rws
b4689000-b4911000 r--s 00000000 08:08 613510     /var/lib/aspell/en-common.rws
b4911000-b4950000 r-xp 00000000 08:08 17468      /usr/lib/libhunspell-1.2.so.0.0.0
b4950000-b4951000 r--p 0003e000 08:08 17468      /usr/lib/libhunspell-1.2.so.0.0.0
b4951000-b4955000 rw-p 0003f000 08:08 17468      /usr/lib/libhunspell-1.2.so.0.0.0
b4962000-b496a000 r-xp 00000000 08:08 157223     /usr/lib/enchant/libenchant_hspell.so
b496a000-b496b000 r--p 00007000 08:08 157223     /usr/lib/enchant/libenchant_hspell.so
b496b000-b496d000 rw-p 00008000 08:08 157223     /usr/lib/enchant/libenchant_hspell.so
b496d000-b497a000 r-xp 00000000 08:08 856859     /lib/libgcc_s.so.1
b497a000-b497b000 r--p 0000c000 08:08 856859     /lib/libgcc_s.so.1
b497b000-b497c000 rw-p 0000d000 08:08 856859     /lib/libgcc_s.so.1
b497c000-b4a60000 r-xp 00000000 08:08 23756      /usr/lib/libstdc++.so.6.0.10
b4a60000-b4a64000 r--p 000e3000 08:08 23756      /usr/lib/libstdc++.so.6.0.10
b4a64000-b4a65000 rw-p 000e7000 08:08 23756      /usr/lib/libstdc++.so.6.0.10
b4a65000-b4a6b000 rw-p b4a65000 00:00 0 
b4a6b000-b4aff000 r-xp 00000000 08:08 22349      /usr/lib/libaspell.so.15.1.4
b4aff000-b4b02000 r--p 00093000 08:08 22349      /usr/lib/libaspell.so.15.1.4
b4b02000-b4b03000 rw-p 00096000 08:08 22349      /usr/lib/libaspell.so.15.1.4
b4b03000-b4b07000 rw-p b4b03000 00:00 0 
b4b07000-b4b09000 r-xp 00000000 08:08 66240      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4b09000-b4b0a000 r--p 00001000 08:08 66240      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4b0a000-b4b0b000 rw-p 00002000 08:08 66240      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4b0b000-b4ba3000 r--p 00000000 08:08 229063     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf

```

---

