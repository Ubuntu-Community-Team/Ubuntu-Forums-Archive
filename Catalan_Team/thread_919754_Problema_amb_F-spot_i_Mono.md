---
title: "Problema amb F-spot i Mono"
date: 2008-09-14
forum: Catalan Team
---

### Post by canroca on 2008-09-14
Hola a tots;

Porto des de fa un temps utilitzant F-Spot com gestor de fotografies. Avui després de descarregar el contingut d'una memòria USB amb fotografies i canviar el nom de la carpeta abans de fer la importació a F-Spot se m'ha tancat l'aplicació.
Quan he tornat a engegar-la, arrenca i es tanca al cab d'un segon.
He re-iniciat l'ordinador varies vegades però el resultat es el mateix.
He desinstal·lat l'aplicació i tornat a instalar.
Finalment he intentat executar-lo des del terminal i el resultat es el seguent l'enganxo a baix. 
Algú te alguna idea de que pot estar pasant?

(/usr/lib/f-spot/f-spot.exe:6467): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.16.4/gobject/gtype.c:2248: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/f-spot/f-spot.exe:6467): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/f-spot/f-spot.exe:6467): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0xffffffff>
  at GConf.Client..ctor () <0x0003b>
  at FSpot.GConfPreferenceBackend.get_Client () <0x0001f>
  at FSpot.GConfPreferenceBackend.AddNotify (string,FSpot.NotifyChangedHandler) <0x00033>
  at FSpot.Preferences.get_Backend () <0x000ea>
  at FSpot.Preferences.Get (string) <0x00074>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    f-spot [0x816b1fa]
    f-spot [0x807de81]
    [0xb7f6e440]
    /usr/lib/libgconf-2.so.4(gconf_client_get_default+0xa9) [0xb6c5b9f9]
    [0xb77cade0]
    [0xb77ca87c]
    [0xb77ca818]
    [0xb77ca764]
    [0xb77ca633]
    [0xb77ca17d]
    [0xb77c693d]
    [0xb77c61c4]
    f-spot(mono_runtime_exec_main+0x10e) [0x809c68e]
    f-spot(mono_runtime_run_main+0x173) [0x809c933]
    f-spot(mono_main+0x6a9) [0x805acd9]
    f-spot [0x805a122]
    /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d1d450]
    f-spot [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7cc5940 (LWP 6467)]
[New Thread 0xb723fb90 (LWP 6469)]
[New Thread 0xb7f5ab90 (LWP 6468)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f6e410 in __kernel_vsyscall ()
  3 Thread 0xb7f5ab90 (LWP 6468)  0xb7f6e410 in __kernel_vsyscall ()
  2 Thread 0xb723fb90 (LWP 6469)  0xb7f6e410 in __kernel_vsyscall ()
  1 Thread 0xb7cc5940 (LWP 6467)  0xb7f6e410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7f5ab90 (LWP 6468)):
#0  0xb7f6e410 in __kernel_vsyscall ()
#1  0xb7e88196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7e804fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7ddde5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb723fb90 (LWP 6469)):
#0  0xb7f6e410 in __kernel_vsyscall ()
#1  0xb7e84aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7e804fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7ddde5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7cc5940 (LWP 6467)):
#0  0xb7f6e410 in __kernel_vsyscall ()
#1  0xb7e8799b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f0435d in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7f047af in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7f051ad in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7f0566c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0816b295 in ?? ()
#7  0x0807de81 in ?? ()
#8  <signal handler called>
#9  0xb6c58423 in ?? () from /usr/lib/libgconf-2.so.4
#10 0xb6c5b9f9 in gconf_client_get_default () from /usr/lib/libgconf-2.so.4
#11 0xb77cade0 in ?? ()
#12 0xb77ca87c in ?? ()
#13 0xb77ca818 in ?? ()
#14 0xb77ca764 in ?? ()
#15 0xb77ca633 in ?? ()
#16 0xb77ca17d in ?? ()
#17 0xb77c693d in ?? ()
#18 0xb77c61c4 in ?? ()
#19 0x0809c68e in mono_runtime_exec_main ()
#20 0x0809c933 in mono_runtime_run_main ()
#21 0x0805acd9 in mono_main ()
#22 0x0805a122 in ?? ()
#23 0xb7d1d450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#24 0x0805a091 in ?? ()
#0  0xb7f6e410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by Rubunter on 2008-09-15
Jo porto tenint aquest problema des que vaig començar amb l'Ubuntu 7.10. M'he passat al Picasa de Google i va perfecte. Si el F-Spot funcionés, però, possiblement el tornaria a utilitzar.

---

