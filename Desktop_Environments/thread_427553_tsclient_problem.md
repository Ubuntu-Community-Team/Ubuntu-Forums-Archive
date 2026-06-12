---
title: "tsclient problem"
date: 2007-04-29
forum: Desktop Environments
---

### Post by RikoW on 2007-04-29
Dear all,

recently (don't exactly know since when), I cannot connect to my windows boxes anymore using the terminal server client 'tsclient'. The rdesktop connection itself works fine when using the command line (I defined some dedicated launchers for the standard connection). It almost seems like, tsclient is generating the wrong rdesktop commands, because the error message I get is the rdesktop error message:

```

> tsclient

** (tsclient:23037): WARNING **:
rdesktop: A Remote Desktop Protocol client.
Version 1.4.1. Copyright (C) 1999-2005 Matt Chapman.
See http://www.rdesktop.org/ for more information.

Usage: /usr/bin/rdesktop [options] server[:port]
   -u: user name
   -d: domain
   -s: shell
   -c: working directory
   -p: password (- to prompt)
   -n: client hostname
   -k: keyboard layout on server (en-us, de, sv, etc.)
   -g: desktop geometry (WxH)
   -f: full-screen mode
   -b: force bitmap updates
   -L: local codepage
   -B: use BackingStore of X-server (if available)
   -e: disable encryption (French TS)
   -E: disable encryption from client to server
   -m: do not send motion events
   -C: use private colour map
   -D: hide window manager decorations
   -K: keep window manager key bindings
   -S: caption button size (single application mode)
   -T: window title
   -N: enable numlock syncronization
   -X: embed into another window with a given id.
   -a: connection colour depth
   -z: enable rdp compression
   -x: RDP5 experience (m[odem 28.8], b[roadband], l[an] or hex nr.)
   -P: use persistent bitmap caching
   -r: enable specified device redirection (this flag can be repeated)
         '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1
             or      COM1=/dev/ttyS0,COM2=/dev/ttyS1
         '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share
             or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'
         '-r clientname=<client name>': Set the client name displayed
             for redirected disks
         '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1
             or      LPT1=/dev/lp0,LPT2=/dev/lp1
         '-r printer:mydeskjet': enable printer redirection
             or      mydeskjet="HP LaserJet IIIP" to enter server driver as well         '-r sound:[local|off|remote]': enable sound redirection
                     remote would leave sound on server
   -0: attach to console
   -4: use RDP version 4
   -5: use RDP version 5 (default)


>

```

As said, doing rdesktop host works just fine?

Any ideas?

Thanks,

                Riko

---

### Post by RikoW on 2007-04-30
Nevermind, I screwed it up myself.

I had put a script called 'rdesktop' in /usr/local/bin which took care of the opacity problem when using beryl looking like that:

```
#!/bin/tcsh
#
setenv XLIB_SKIP_ARGB_VISUALS 1
/usr/bin/rdesktop $*

```

I assume, tsclient was executing that script, but the options were not passed along properly.

After renaming the script, everthing works again. :)

Cheers,

                     Riko

---

### Post by chavash on 2008-01-31
Hello! I can't hear any sound using tsclient. I tested everything, but it doesn't help. Any ideas?

---

