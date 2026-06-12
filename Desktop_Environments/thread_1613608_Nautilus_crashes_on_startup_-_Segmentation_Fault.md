---
title: "Nautilus crashes on startup - Segmentation Fault?"
date: 2010-11-04
forum: Desktop Environments
---

### Post by askates on 2010-11-04
I've been having a bit of trouble with Nautilus for the past few days; as soon as I log in, Nautilus starts opening "Starting file manager" windows uncontrollably, and I have to 'killall nautilus' to stop it.

If I try and run nautilus from the terminal, I'm merely given the output: 
```
Segmentation fault
```I tried using Backtrace to find out what went wrong, but to be honest, I don't really know what I'm looking at.

```
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/nautilus...(no debugging symbols found)...done.
(gdb) handle SIG33 pass notstop noprint
Unrecognised or ambiguous flag word: "notstop".
(gdb) handle SIG33 nostop noprint
Signal        Stop    Print    Pass to program    Description
SIG33         No    No    Yes        Real-time event 33
(gdb) set pagination 0
(gdb) run
Starting program: /usr/bin/nautilus 
[Thread debugging using libthread_db enabled]

Program received signal SIGSEGV, Segmentation fault.
0x014b25a0 in XF86DRIQueryExtension () from /usr/lib/fglrx/libGL.so.1
(gdb) backtrace fun[Kll
#0  0x014b25a0 in XF86DRIQueryExtension () from /usr/lib/fglrx/libGL.so.1
No symbol table info available.
#1  0x0000000f in ?? ()
No symbol table info available.
(gdb) info registers
eax            0x41    65
ecx            0x821c188    136429960
edx            0x1506500    22045952
ebx            0x8259a90    136682128
esp            0xbfffcf20    0xbfffcf20
ebp            0x8216598    0x8216598
esi            0x0    0
edi            0x1    1
eip            0x14b25a0    0x14b25a0 <XF86DRIQueryExtension+142>
eflags         0x10202    [ IF RF ]
cs             0x73    115
ss             0x7b    123
ds             0x7b    123
es             0x7b    123
fs             0x0    0
gs             0x33    51
(gdb) x/16i $pc
=> 0x14b25a0 <XF86DRIQueryExtension+142>:    movzbl 0x4(%esi),%edx
   0x14b25a4 <XF86DRIQueryExtension+146>:    mov    %dl,(%ecx)
   0x14b25a6 <XF86DRIQueryExtension+148>:    mov    %al,0x1(%ecx)
   0x14b25a9 <XF86DRIQueryExtension+151>:    xor    %ecx,%ecx
   0x14b25ab <XF86DRIQueryExtension+153>:    lea    (%esp),%eax
   0x14b25ae <XF86DRIQueryExtension+156>:    push   %ecx
   0x14b25af <XF86DRIQueryExtension+157>:    push   %ecx
   0x14b25b0 <XF86DRIQueryExtension+158>:    push   %eax
   0x14b25b1 <XF86DRIQueryExtension+159>:    push   %ebp
   0x14b25b2 <XF86DRIQueryExtension+160>:    call   0x41af30 <_XReply>
   0x14b25b7 <XF86DRIQueryExtension+165>:    add    $0x10,%esp
   0x14b25ba <XF86DRIQueryExtension+168>:    test   %eax,%eax
   0x14b25bc <XF86DRIQueryExtension+170>:    jne    0x14b25da <XF86DRIQueryExtension+200>
   0x14b25be <XF86DRIQueryExtension+172>:    mov    0x4d0(%ebp),%eax
   0x14b25c4 <XF86DRIQueryExtension+178>:    test   %eax,%eax
   0x14b25c6 <XF86DRIQueryExtension+180>:    je     0x14b25cd <XF86DRIQueryExtension+187>
(gdb) thread apply all backtrace

Thread 1 (Thread 0xb7fd9870 (LWP 2427)):
#0  0x014b25a0 in XF86DRIQueryExtension () from /usr/lib/fglrx/libGL.so.1
#1  0x0000000f in ?? ()
(gdb) quit
```

---

### Post by mateomiguel on 2010-11-05
I've been having this exact same problem.  Uncontrollable Nautilus windows opening on boot up.  I was able to track down a way to stop them from opening, which was to change a setting in nautilus.desktop from autorestart True to autorestart false.  But now when I boot up i get a black screen which cannot be clicked on for my wallpaper, and nothing else.  This seems like a very basic problem.  I have no idea what to do with it.  Does anybody else know?

---

### Post by askates on 2010-11-07
Can anyone try and shed some light on this? It's somewhat annoying to not be able to access any folders via the GUI.

---

### Post by askates on 2010-11-09
Edit: Okay, seeing how no-one has even attempted to help me, will I be able to get access to my files and folders if I install another file manager? Not being able to view my folders is starting to **** me off.

---

### Post by peertop on 2010-11-25
I had the same problem with infinite nautilus loops,
I got the problem when I installed fglrx for my radeon x300 gpu.
The gpu and fglrx did not worked with mavericks xorg , and that caused my problems.
And like you I could not restart nautilus after I killed it.

In my case It was easy solved with remove the fglrx driver.
and after nextcoming reboot nautilus was working nice again.

---

### Post by Helkaluin on 2010-11-25
> **askates said:**
> 

```

0x014b25a0 in XF86DRIQueryExtension () from /usr/lib/fglrx/libGL.so.1
(gdb) backtrace fun[Kll
#0  0x014b25a0 in XF86DRIQueryExtension () from /usr/lib/fglrx/libGL.so.1
No symbol table info available.

```
It's fglrx. Try downgrading or disabling that?

EDIT: Do you have x-swat or xorg-edgers enabled?

---

