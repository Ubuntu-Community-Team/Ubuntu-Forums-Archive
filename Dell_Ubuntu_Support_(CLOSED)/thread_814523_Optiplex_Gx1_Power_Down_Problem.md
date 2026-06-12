---
title: "Optiplex Gx1 Power Down Problem"
date: 2008-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mtgo29 on 2008-05-31
Hi Guys,

I have a Power Down problem!
I'm running hardy heron 8.04 on a Dell Optiplex Gx1 Pentium 3 (Katmai) 447.704mhz.
[COLOR="Red"]Problem:[/COLOR] when Logging off then shutdown [COLOR="Red"]"it doesn't[/COLOR] [COLOR="Red"]shut down"[/COLOR] it hangs and the only way to shut it down is to press the power down button.I didn't have this problem with Gutsy 7.10 or earlier releases.Any help is much appreciated.:(
Thanks




Ubuntu User #15804

---

### Post by FakeOutdoorsman on 2009-01-15
I had this issue with Debian Etch, and was previously able to power down with CentOS 4.  All I had to do was enable ACPI in the BIOS.  I didn't have to add any extra kernel parameters to GRUB.  I also disabled Power Management in the BIOS, but I doubt that has much to do with it, but maybe.  It is a headless command-line only machine and I turn it off with:
```
shutdown -h now
```
The auto power-on in the BIOS is a useful feature.  I use it to start the computer to make daily database backups and then the script runs the above shutdown code (shutdown for that user has been added to the sudoers file, so no password needed) which turns off the computer nicely.

I'm using BIOS A09.  I think A10 might be the final version, but I am unsure.  I used this thread to upgrade from A07 (although I suppose most GX1 BIOS versions should work):
[HOWTO: Flash BIOS, The Ubuntu Way](http://ubuntuforums.org/showthread.php?t=318789)

---

### Post by mtgo29 on 2009-05-11
Sorry for the late reply!! but Thank you [COLOR="Blue"]FakeOutdoorsman[/COLOR] yes I followed your fix and it's fixed :guitar:
Thank you...........

Ubuntu User #15804

---

