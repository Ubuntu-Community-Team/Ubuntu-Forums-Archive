---
title: "Error message: hub 8-0:1.0: unable to enumerate USB device on port 4?"
date: 2008-12-30
forum: General Help
---

### Post by Strid on 2008-12-30
I have the following errormessage, which keeps popping up when I'm in a console (Ctrl-Alt-F#), or when I write "dmesg".
If I'm in a console, it's impossible to use it, since every 1/5th of a second or so, a new line with the error message pops up, so you can't see what you're writing.

Looks something like this an just keeps on posting a new line all the time. As you can see on the timestamp to the left, there's about 0.2 second between every message! Really annoying.

```

...
[  229.756218] hub 8-0:1.0: unable to enumerate USB device on port 4
[  229.944232] hub 8-0:1.0: unable to enumerate USB device on port 4
[  230.132233] hub 8-0:1.0: unable to enumerate USB device on port 4
[  230.320232] hub 8-0:1.0: unable to enumerate USB device on port 4
...

```


I tried to disconnect all USB devices, save an internal cardreader. But that didn't solve the problem. I have no idea what's wrong. I get the problem even if I boot from a fresh Ubuntu CD, nothing installed. It's the same under 32-bit and 64-bit. (Currently running 64-bit Ibex 8.10)

```

strid@helium:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 007 Device 002: ID 041e:3100 Creative Technology, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0924:3d60 Xerox 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

If it gives any more clues, USB transfer speeds are really slow also. Probably around few kb/s.

Does anyone have a diagnosis or a solution? In which log file do I look for error messages?

Thanks,
Strid

---

### Post by Strid on 2009-01-02
Bumpety bump!

:popcorn:

---

