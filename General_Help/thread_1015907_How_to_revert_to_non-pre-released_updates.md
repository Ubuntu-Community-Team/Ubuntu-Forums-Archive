---
title: "How to revert to non-pre-released updates?"
date: 2008-12-19
forum: General Help
---

### Post by Ursa on 2008-12-19
Ubuntu Intrepid
ATI Radeon X1950 Pro (PCIe)

I read in a thread that a possible fix for my graphics problems would be to check the "download pre-released updates" and update all in synaptic.
This however resulted in nothing but "x-server start failed" when booting and the only way to interact with Ubuntu is via the CLI.
I get three kernel versions to choose from when I boot,
something-10-something <-- this one is new after the "update"
something-9-something <-- I used this before
something-7-something

I don't remember the exact lines but I don't think it's important, I'll gladly check if it's necessary.

I've been trying to fix the graphics all week and I've only moved backwards, I'm really looking for how to uninstall the pre-released updates from the CLI so I can at least get into the GUI.

Any help with the graphics would also be appreciated, I haven't had much luck before.

(I'm not that experienced with Linux but I've poked around quite a bit and I'm very comfortable with bash. I'm not afraid to learn and try new stuff either, so bring it on) :)

Thanks in advance.

---

### Post by sdennie on 2008-12-19
Rather than removing the updates, you can select an older kernel from the boot list and that should fix your problem.

---

### Post by Ursa on 2008-12-19
I tried that, there's no difference.
Hmm, the error occured when I updated to 2.6.27-10-generic, but it's still there when I try the other versions... What does this mean?

I ran these:

```
$ fglrxinfo
Error: unable to open display (null)
```

```
$ ./compiz-check
[...]
Unable to detect fglrx driver version

```

I've tried fixing broken dependencies and x-server from recovery mode to no avail, I just end up where I started.

I've tried reinstalling xorg and x-server.

I've basically tried everything related I found on these forums and google.

I feel a bit stuck, but I'm not giving up! :D

Oh, maybe I should point out that the output from those two commands up there have been the same no matter what I've tried or where I've been in the process. I've run them "a few" times.

---

