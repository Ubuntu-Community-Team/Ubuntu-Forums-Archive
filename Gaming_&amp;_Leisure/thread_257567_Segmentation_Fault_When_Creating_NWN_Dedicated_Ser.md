---
title: "Segmentation Fault When Creating NWN Dedicated Server in Ubuntu 6.06 Server Edition"
date: 2006-09-14
forum: Gaming &amp; Leisure
---

### Post by usechoosername on 2006-09-14
I continuously got a Segmentation fault when trying to start up NWN running the Chapter1 module.  After many hours of searching in vain for help on google, I decided to see what the "man" command could do for me.  So I used "apropos" to find a manual entry containing "segmentation fault" and found the command "catchsegv."  So I used it to provide more specific information about the nature of the problem so that if someone should have the know-how to help me they'd be left with less questions.  So here goes . . .
---------------------------------------------------------------------------
admin@HomeServer:~$ cd /home/admin/NWN
admin@HomeServer:~/NWN$ catchsegv ./nwserver -module Chapter1
Neverwinter Nights Server
Build:8099
Copyright BioWare Corp 1998-2004

Server: Loading...
Server: Running...

Server: Loading module "Chapter1"..*** Segmentation fault
Register dump:

 EAX: 00002330   EBX: 0e0a3928   ECX: 0dc6ea00   EDX: 00000000
 ESI: 0000001f   EDI: 0dce70b0   EBP: bf8f7ec8   ESP: bf8f7ec8

 EIP: 082bf850   EFLAGS: 00010206

 CS: 0073   DS: 007b   ES: 007b   FS: 0000   GS: 0033   SS: 007b

 Trap: 0000000e   Error: 00000004   OldMask: 00000000
 ESP/signal: bf8f7ec8   CR2: 00002338

 FPUCW: ffff037f   FPUSW: ffff0020   TAG: ffffffff
 IPOFF: 08165203   CSSEL: 0073   DATAOFF: 0e0a3694   DATASEL: 007b

 ST(0) 0000 0000000000000000   ST(1) 0000 0000000000000000
 ST(2) 0000 0000000000000000   ST(3) 0000 0000000000000000
 ST(4) 0000 a000000000000000   ST(5) 0000 f000000000000000
 ST(6) 0000 f000000000000000   ST(7) 0000 0000000000000000

Backtrace:
/lib/libSegFault.so[0xb7fdf2ae]
[0xffffe420]
[0x82ac4bf]
[0x82aa502]
[0x82ae674]
[0x8232b77]
[0x8166fc6]
[0x80ce165]
[0x80cd9ad]
[0x80cc6b3]
[0x81b6256]
[0x80a041c]
./nwserver(__strtod_internal+0x3e73)[0x804e747]
./nwserver(__strtod_internal+0x297d)[0x804d251]
./nwserver(strftime+0xdd3)[0x804b957]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2)[0xb7e84ea2]
./nwserver(read+0x4d)[0x804b191]

Memory map:

08048000-08329000 r-xp 00000000 03:01 3932184 /home/admin/NWN/nwserver
08329000-083c9000 rwxp 002e0000 03:01 3932184 /home/admin/NWN/nwserver
083c9000-0e1bc000 rwxp 083c9000 00:00 0 [heap]
b6907000-b6910000 r-xp 00000000 03:01 1736719 /lib/libgcc_s.so.1
b6910000-b6911000 rwxp 00009000 03:01 1736719 /lib/libgcc_s.so.1
b691b000-b699c000 rwxp b691b000 00:00 0
b699d000-b6b02000 rwxp b699d000 00:00 0
b6b02000-b6b12000 r-xp 00000000 03:01 1736944 /lib/tls/i686/cmov/libresolv-2.3.6.so
b6b12000-b6b13000 rwxp 00010000 03:01 1736944 /lib/tls/i686/cmov/libresolv-2.3.6.so
b6b13000-b6b15000 rwxp b6b13000 00:00 0
b6b15000-b6b1e000 r-xp 00000000 03:01 1736910 /lib/tls/i686/cmov/libnss_files-2.3.6.so
b6b1e000-b6b1f000 rwxp 00008000 03:01 1736910 /lib/tls/i686/cmov/libnss_files-2.3.6.so
b6b29000-b6b2a000 ---p b6b29000 00:00 0
b6b2a000-b766e000 rwxp b6b2a000 00:00 0
b766e000-b766f000 ---p b766e000 00:00 0
b766f000-b7e70000 rwxp b766f000 00:00 0
b7e70000-b7f95000 r-xp 00000000 03:01 1736900 /lib/tls/i686/cmov/libc-2.3.6.so
b7f95000-b7f9c000 rwxp 00125000 03:01 1736900 /lib/tls/i686/cmov/libc-2.3.6.so
b7f9c000-b7f9f000 rwxp b7f9c000 00:00 0
b7f9f000-b7fae000 r-xp 00000000 03:01 1736918 /lib/tls/i686/cmov/libpthread-2.3.6.so
b7fae000-b7faf000 rwxp 0000e000 03:01 1736918 /lib/tls/i686/cmov/libpthread-2.3.6.so
b7faf000-b7fb2000 rwxp b7faf000 00:00 0
b7fb2000-b7fd3000 r-xp 00000000 03:01 1736904 /lib/tls/i686/cmov/libm-2.3.6.so
b7fd3000-b7fd4000 rwxp 00020000 03:01 1736904 /lib/tls/i686/cmov/libm-2.3.6.so
b7fd7000-b7fdb000 r-xp 00000000 03:01 1736909 /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b7fdb000-b7fdc000 rwxp 00003000 03:01 1736909 /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b7fdc000-b7fde000 rwxp b7fdc000 00:00 0
b7fde000-b7fe1000 r-xp 00000000 03:01 1736743 /lib/libSegFault.so
b7fe1000-b7fe2000 rwxp 00002000 03:01 1736743 /lib/libSegFault.so
b7fe2000-b7fe5000 rwxp b7fe2000 00:00 0
b7fe5000-b7ffa000 r-xp 00000000 03:01 1736720 /lib/ld-2.3.6.so
b7ffa000-b7ffb000 rwxp 00014000 03:01 1736720 /lib/ld-2.3.6.so
bf8e5000-bf8fa000 rwxp bf8e5000 00:00 0 [stack]
ffffe000-fffff000 ---p 00000000 00:00 0 [vdso]
---------------------------------------------------------------------------
And in case you were wondering:

admin@HomeServer:~$ cd /home/admin/NWN
admin@HomeServer:~/NWN$ ./fixinstall
Checking for required files

PASSED: data directory exists
PASSED: nwm directory exists
PASSED: chitin.key exists
PASSED: dialog.tlk exists
PASSED: nwserver exists

Fixing case

data
............
hak
.
override
.

Checking for problem files


Checking for permissions

PASSED: nwnplayer.ini is writable
PASSED: saves is writable
PASSED: /home/admin/NWN is writable

You are ready to run Neverwinter Nights.

---------------------------------------------------------------------------

ANY HELP would be greatly appreciated!  THANK YOU!

---

### Post by Badjaccur on 2007-03-18
Same problem here. Any news?

---

