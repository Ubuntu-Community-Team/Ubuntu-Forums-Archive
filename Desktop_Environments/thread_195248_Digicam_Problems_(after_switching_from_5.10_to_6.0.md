---
title: "Digicam Problems (after switching from 5.10 to 6.06)"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Franko30 on 2006-06-12
Hello everybody,

EDIT: This problem was solved with the new 2.6.15-25-686 kernel that came via the updates.

[COLOR="Blue"]I'm experiencing problems accessing my Sony DSC-F828 after switching from Ubuntu 5.10 to 6.06 (new install).[/COLOR]

The problem occurs on a Dell Latitude X1, as well as on a Sony PCG-SRX51P laptop.

**Problem:**

In Ubuntu 5.10 I could access my camera without problems in PTP mode: gthmb would pop-up and invite me to copy the photos.

On both laptops (after installing 6.06) nothing happens anymore. gthumb as well as gtkam don't find a camera.

```
less kern.log
``` in /var/log delivers results like:

```
Jun 12 22:31:21 localhost kernel: [4295684.342000] usb 1-1: new full speed USB device using uhci_hcd and address 61
Jun 12 22:31:22 localhost kernel: [4295684.766000] usb 1-1: device not accepting address 61, error -71

```

As this happens on two different machines, I guess it is an Ubuntu 6.06 bug.

Maybe these threads:

[http://www.ubuntuforums.org/showthread.php?t=194645&highlight=sony](http://www.ubuntuforums.org/showthread.php?t=194645&highlight=sony)
and
[http://www.ubuntuforums.org/showthread.php?t=193353&highlight=sony](http://www.ubuntuforums.org/showthread.php?t=193353&highlight=sony)

describe the same problem...

Any help would be appreciated.

Thanks in advance!

Franko30

---

### Post by Franko30 on 2006-06-13
[QUOTE=Franko30]As this happens on two different machines, I guess it is an Ubuntu 6.06 bug.
[/QUOTE]

Well, I solved the case for myself:

[COLOR="Blue"]I found something else, that both laptops have in common in addition to Ubuntu 6.06: linux-686 (the 686 instead of the 386 standard kernel).

When starting with the 686 kernel I get the error messages given above.

When I start Ubuntu 6.06 with the 386 kernel, I can plug in my digital camera as before in 5.10 and everything works fine: I can import my pictures (now even in usual USB mass storage mode, not only in PTP mode).
[/COLOR]

As this is related to the linux-686 kernel, I still consider this as a bug (in 5.10 with the 686 kernel, everything worked fine).

Cheers

Franko30

---

### Post by kingmonkey on 2006-06-15
Did you report this bug?

---

### Post by Franko30 on 2006-06-19
Hi,

no, I didn't  report a bug, as I don't know where and how.

And I'm pretty sure I might mix up categories etc. when doing so.

Can you help me with this?

[B]EDIT: It seems to be solved with the new kernel 2.6.15-25-686 that came via the updates.

On the other hand, the bug in the 686 kernel that keeps the CPU load high around 50% on Pentium M processors is still present... :-([/B]

Thanks in advance

Franko30

---

