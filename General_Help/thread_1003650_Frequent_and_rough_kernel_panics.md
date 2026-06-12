---
title: "Frequent and rough kernel panics"
date: 2008-12-06
forum: General Help
---

### Post by Charlie708 on 2008-12-06
I'm having problems with frequent kernel panics.  I am running 8.10 i386.  The problem started with 2.6.27-7-generic, and continues with 27-9-generic.  However, my problem is that I can't find any useful data from the logs.  faillog is corrupt, and seems to contain nothing but '@^' in no locale.  Looking through the syslog is also useless, it has nothing about the crash.

My system crashed at 11:53 last night, and here is the syslog report:
```

Dec  5 23:31:00 t400 kernel: [  100.644062] ath0: no IPv6 routers present
Dec  5 23:39:10 t400 kernel: [  590.782803] wifi0: FAILED verification of AR5K_PHY_SIG_FIRPWR default value [found=0x0 (0) expected=0xba (-70)].
Dec  5 23:39:10 t400 kernel: [  590.782837]               (unknown):0x9858:0x0000002e:........ ........ ........ ..1.111.:unknown
Dec  5 23:49:49 t400 -- MARK --
Dec  5 23:53:07 t400 syslogd 1.5.0#2ubuntu6: restart.

```
The error report is suspicious, but it happens 14 minutes before the crash.  I think it is being caused by the wireless card being deactivated by a hardware switch.

The only thing I could pull from the logs was a glibc error on a normal shutdown:
```

Dec  5 18:53:29 t400 x-session-manager[5986]: GLib-CRITICAL: g_key_file_load_from_dirs: assertion `!g_path_is_absolute (file)' failed 
Dec  5 18:53:29 t400 x-session-manager[5986]: ******************* START ********************************
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 0: x-session-manager [0x805d9f5]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 1: x-session-manager [0x805dba4]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 2: [0xb7f84400]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 3: x-session-manager [0x805b731]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 4: x-session-manager [0x805fcc8]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 5: /usr/lib/libglib-2.0.so.0 [0xb78fefa5]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 6: x-session-manager [0x805fb5e]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 7: x-session-manager [0x805bc15]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 8: /usr/lib/libgobject-2.0.so.0(g_object_newv+0x376) [0xb799ac06]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 9: /usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x2e2) [0xb799b802]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 10: /usr/lib/libgobject-2.0.so.0(g_object_new+0x6e) [0xb799b94e]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 11: x-session-manager [0x805a0a1]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 12: x-session-manager [0x8062fca]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 13: /usr/lib/libglib-2.0.so.0 [0xb790ce26]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 14: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8) [0xb790c6f8]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 15: /usr/lib/libglib-2.0.so.0 [0xb790fda3]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 16: /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d2) [0xb79102c2]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 17: /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb7c4e3a9]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 18: x-session-manager [0x805f629]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 19: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7678685]
Dec  5 18:53:29 t400 x-session-manager[5986]: Frame 20: x-session-manager [0x8050591]
Dec  5 18:53:29 t400 x-session-manager[5986]: ******************* END **********************************
Dec  5 18:53:29 t400 init: tty4 main process (4758) killed by TERM signal
Dec  5 18:53:29 t400 init: tty5 main process (4759) killed by TERM signal
Dec  5 18:53:29 t400 init: tty2 main process (4762) killed by TERM signal
Dec  5 18:53:29 t400 init: tty3 main process (4764) killed by TERM signal
Dec  5 18:53:29 t400 init: tty6 main process (4766) killed by TERM signal
Dec  5 18:53:29 t400 init: tty1 main process (5864) killed by TERM signal
Dec  5 18:53:29 t400 kernel: [ 6276.008656] apm: BIOS not found.
Dec  5 18:53:29 t400 xfs[5424]: terminating 
Dec  5 18:53:32 t400 kernel: [ 6279.267916] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec  5 18:53:34 t400 bluetoothd[5628]: bridge pan0 removed
Dec  5 18:53:34 t400 bluetoothd[5628]: Stopping SDP server
Dec  5 18:53:34 t400 bluetoothd[5628]: Exit
Dec  5 18:53:34 t400 avahi-daemon[5150]: Got SIGTERM, quitting.
Dec  5 18:53:34 t400 avahi-daemon[5150]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.109.
Dec  5 18:53:34 t400 exiting on signal 15

```

I am running a T400 with Intel only GPU, and two Atheros cards (AR5007-EG, AR5008E-3NX) with Madwifi 0.10.5.6 patched for packet injection.  ath0 is the AR5008, and ath1 is the AR5007, but it is not currently running.

Crashing tends to happen when I am working in OpenOffice, or browsing the web with FireFox.  Anyone now how to fix this?

---

