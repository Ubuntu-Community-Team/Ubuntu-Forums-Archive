---
title: "Nautilus Crash"
date: 2008-05-14
forum: Desktop Environments
---

### Post by damonjablons on 2008-05-14
Hi,

I have a fresh Ubuntu installation (I recently reformatted), and for some reason whenever I try to drag and drop a folder from nautilus into another instance of nautilus (at another location), my computer crashes.

Is this bug report worthy?

Anything I can print here to help solve this?

Thanks in advance,
Damon J.

---

### Post by damonjablons on 2008-05-14
**update:** it seems that it's actually the drag and drop *into* nautilus which crashes the machine.  even when dragging files from the desktop, it has the same effect.  not just folders, but any type of file.  of course moving files via the terminal does not have the same effect.

-d

---

### Post by Awalton on 2008-05-14
Please obtain a [Backtrace](https://wiki.ubuntu.com/Backtrace) of the crash and file a bug on Launchpad, thanks.

---

### Post by damonjablons on 2008-05-14
When I follow the tutorial on the link provided, it doesn't produce a txt document in my home directory.  My guess is that I have to recreate the crash or something?  Maybe I have to run arguments at the end?  Please help.  Thanks.

---

### Post by Awalton on 2008-05-14
> **damonjablons said:**
> When I follow the tutorial on the link provided, it doesn't produce a txt document in my home directory.  My guess is that I have to recreate the crash or something?  Maybe I have to run arguments at the end?  Please help.  Thanks.

If nautilus is already running, you should kill it first (nautilus -q should be sufficient), then you can start debugging it.

And yes, you do need to reproduce the crash: **The program will start. Perform any actions necessary to reproduce the crash**. Else we have nothing to work with.

---

### Post by damonjablons on 2008-05-14
When this crash occurs, my entire computer crashes.  How can I execute the commands that force the backtrace after I've recreated the crash if my computer crashes?

---

### Post by damonjablons on 2008-05-14
Since I couldn't perform the backtrace, here's what's in the text file I have

```


GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) handle SIG33 pass nostop noprint
Signal        Stop	Print	Pass to program	Description
SIG33         No	No	Yes		Real-time event 33
(gdb) setpa[K[K pagination 0
(gdb) run
Starting program: /usr/bin/nautilus 
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb6ac7720 (LWP 6606)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 0xb692db90 (LWP 6609)]

Program exited normally.
(gdb) Hangup detected on fd 0
Error detected on fd 0
error detected on stdin

```

is this sufficient?

---

### Post by Awalton on 2008-05-14
Nautilus shouldn't be able to hang your whole computer like that under any circumstance... File a bug on Launchpad against Ubuntu and give explicit, detailed instructions of how to reproduce the crash, along with your hardware information, graphics drivers, any valid information in your Xorg.0.log, and whether or not you're using Compiz. Thanks.

---

### Post by damonjablons on 2008-05-14
I posted the bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/230405](https://bugs.launchpad.net/ubuntu/+bug/230405)

---

