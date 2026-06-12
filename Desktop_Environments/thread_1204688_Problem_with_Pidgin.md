---
title: "Problem with Pidgin"
date: 2009-07-05
forum: Desktop Environments
---

### Post by RoMiONeT on 2009-07-05
[B][SIZE=2]Hello,

i have just instllled Ubuntu 9.04 in my PC .. and i tried to use pidgin , unfortunately there is problem when i log to my mail the contact list became blank and it closed .. i tried to know the error from terminal by typing pidgin
it appears

[/SIZE][SIZE=2][COLOR=Red]Segmentation fault[/COLOR][/SIZE][SIZE=2]

i use Gnome ( ubuntu 9.04 )

Could you please help me ?


Thanks
[/SIZE][/B]

---

### Post by RoMiONeT on 2009-07-05
hello,

could you please see it 

romio@romio-desktop:~$ gdb pidgin
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) handle SIGPIPE nostop noprint
Signal        Stop    Print    Pass to program    Description
SIGPIPE       No    No    Yes        Broken pipe
(gdb) run
Starting program: /usr/bin/pidgin 
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
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
(no debugging symbols found)
[New Thread 0xb7011750 (LWP 10023)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---return  
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---q
Error while reading shared library symbols:
Quit
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

---Type <return> to continue, or q <return> to quit--- q
Error while reading shared library symbols:
Quit
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)


Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7011750 (LWP 10023)]
0xb62c013a in ?? () from /usr/lib/purple-2/libmsn.so
(gdb) bt full
#0  0xb62c013a in ?? () from /usr/lib/purple-2/libmsn.so
No symbol table info available.
#1  0xb62aca3d in msn_cmdproc_process_payload ()
   from /usr/lib/purple-2/libmsn.so
No symbol table info available.
#2  0xb62c59eb in msn_servconn_process_data () from /usr/lib/purple-2/libmsn.so
No symbol table info available.
#3  0xb62c5ba1 in ?? () from /usr/lib/purple-2/libmsn.so
No symbol table info available.
#4  0x080a8e83 in ?? ()
No symbol table info available.
#5  0xb7862dad in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb782bb88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb782f0eb in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb782f5ba in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb7b1e7d9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0x080c31da in main ()
No symbol table info available.
(gdb)

---

