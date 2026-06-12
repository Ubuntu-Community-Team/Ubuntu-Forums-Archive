---
title: "Potato Guy a.k.a. KTuberling will not execute"
date: 2007-07-28
forum: Desktop Environments
---

### Post by Mindslant on 2007-07-28
This counts as a minor family crisis for my house.  When I launch the program via Applications Menu Icon I get a dialog box reading ""Fatal Error:  Unable to load pictures, aborting".

I have un-installed and re-installed the application with restarts with Synaptic.  I sure would appreciate any help.  I like to learn how to troubleshoot the problem and fix it so I become a more competent user.

---

### Post by Mindslant on 2007-07-28
Potato Guy will execute under another user, but I don't see any permissions problems

---

### Post by GeneralZod on 2007-07-28
Try running

```

kbuildsycoca

```

from a terminal, and try again.  This rebuilds KDEs' cache of known applications, plugins, resources and services.

---

### Post by Mindslant on 2007-07-29
Thank you very much for your reply.  Here is what happened when I ran the command.

1st attempt:
zephyr@zephyr-desktop:~$ kbuildsycoca
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!

With the Sudo command:
zephyr@zephyr-desktop:~$ sudo kbuildsycoca
Password:
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kio (KSycoca): ERROR: No database available!
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
zephyr@zephyr-desktop:~$ 

I'm going to assume ERROR means not good.  KTuberling isn't working any better.

---

### Post by fiskz on 2008-01-07
I'm also having the same error message and haven't been successful rebuilding the kde cache. Has anyone else found a solution?

---

### Post by maybeway36 on 2008-01-07
It says that error to me a lot, and stuff seems to woek.
Maybe check ~/.kde/share/apps/ and ~/.kde/share/config/.

---

### Post by GeneralZod on 2008-01-07
> **fiskz said:**
> I'm also having the same error message and haven't been successful rebuilding the kde cache. Has anyone else found a solution?

The error can be ignored - it was found to be cruft from Ancient Times :) I don't know what the source of your problems are, though :/

---

### Post by fiskz on 2008-01-07
I just expanded my filesystem searching with some notes found from other sources. My fix just worked I renamed (rather than delete) ~/.kde/share/config/ktuberlingrc to :~/.kde/share/config/ktuberlingrc080107. 

Potato guy now loads. My 3 year will be happy to discover later.

---

