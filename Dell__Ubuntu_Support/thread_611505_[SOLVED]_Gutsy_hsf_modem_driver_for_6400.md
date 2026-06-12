---
title: "[SOLVED] Gutsy hsf modem driver for 6400"
date: 2007-11-13
forum: Dell  Ubuntu Support
---

### Post by Linicks on 2007-11-13
Dell have finally released the new driver.  I will be trying this tonight after work:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver)

Nick

---

### Post by Linicks on 2007-11-13
Actually, I tried this at work - it doesn't work :-(

The modem just doesn't work, and it also fubars my sound - I have to uninstall it to get sound back...

Nick

---

### Post by neilius on 2007-11-13
Interesting... they say a logout/login or GDM restart clears this. I'm wondering if/when the x86_64 Ubuntu package will be released by Dell! Us 64bit users still exist...

Rgds,

Neil.

---

### Post by Dellfan on 2007-11-13
On the same page they mention 64 bit packages and following the link takes you to a direcotry with both a 64 bit rpm and a tar.gz file.

Linicks can you reinstall it and report back if a logout/login or a GDM restart resolves the sound issue?

---

### Post by jdelaros1 on 2007-11-13
Linicks:

Are you installing the 32-bit desktop package hsfmodem_7.60.00.18oem_i386.deb ?? This package works on the Inspiron 4600, but you have to login/logout to clear the sound issue, as described in the Wiki page.

---

### Post by Linicks on 2007-11-14
The reason it doesn't work for me is due to kernel modules symbols mismatch...

Investigation reveals the snd-hda-intel and snd-hda-codec modules get
built, but hit wrong symbol errors and will not load:

e.g.

```
Nov 13 10:59:20 palantir kernel: [   15.884000] snd_hda_codec: disagrees
about version of symbol snd_ctl_add
Nov 13 10:59:20 palantir kernel: [   15.884000] snd_hda_codec: Unknown
symbol snd_ctl_add
Nov 13 10:59:20 palantir kernel: [   15.884000] snd_hda_codec: disagrees
about version of symbol snd_pcm_kernel_ioctl
Nov 13 10:59:20 palantir kernel: [   15.884000] snd_hda_codec: Unknown
symbol snd_pcm_kernel_ioctl

Nov 13 10:59:20 palantir kernel: [   15.940000] snd_hda_intel: disagrees
about version of symbol snd_pcm_new
Nov 13 10:59:20 palantir kernel: [   15.940000] snd_hda_intel: Unknown
symbol snd_pcm_new
Nov 13 10:59:20 palantir kernel: [   15.940000] snd_hda_intel: disagrees
about version of symbol snd_pcm_limit_hw_ra$
Nov 13 10:59:20 palantir kernel: [   15.940000] snd_hda_intel: Unknown
symbol snd_pcm_limit_hw_rates
Nov 13 10:59:20 palantir kernel: [   15.940000] snd_hda_intel: disagrees
about version of symbol snd_card_register
Nov 13 10:59:20 palantir kernel: [   15.940000] snd_hda_intel: Unknown
symbol snd_card_register
```

I have reported this to Dell.

Nick

---

### Post by neilius on 2007-11-14
> **Dellfan said:**
> On the same page they mention 64 bit packages and following the link takes you to a direcotry with both a 64 bit rpm and a tar.gz file.

They do, but there is no 64 bit .deb package there yet, only the rpm and tarball as you rightly say. I'd rather not do a manual compile/install if I can avoid it! :-)

Rgds,

Neil.

---

### Post by jdelaros1 on 2007-11-14
Linick:

I don't see this on my Inspiron 6400, works fine. Have you downloaded codecs from somewhere or done a special configuration on your system?

---

### Post by Linicks on 2007-11-14
> **jdelaros1 said:**
> Linick:

I don't see this on my Inspiron 6400, works fine. Have you downloaded codecs from somewhere or done a special configuration on your system?

Nope.  I have a Dell pre-installed Ubuntu 7.04.  I upgraded to 7.10 a few weeks ago.

All is standard Ubuntu packages.

Researching, it appears alsa package _could_ cause conflicts - can you tell me please what package versions you have of:

[LIST=1]
[*]alsa-base
[*]any other alsa packages installed (alsa-oss etc.)
[*]kernel version
[*]linux-backport-module versions
[/LIST]

and output of:

```
cat /proc/asound/card0/codec#1
```

Thanks,

Nick

---

### Post by Dellfan on 2007-11-14
You could always use Alien to  convert the .rpm into a .deb

---

### Post by Linicks on 2007-11-14
I am getting warming here.  For some reason, it doesn't build the right snd-hda* stuff on my system, and I smell a BUG.

After I install the new driver, if I run hsfconfig, I get this perculiar message at the end, which I think is where the bug is:


> Building modules for kernel 2.6.22-14-generic, using source directory
/lib/modules/2.6.22-14-generic/build. Please wait...
done.

Warning: no device detected by hsf driver - HDA modems may require reboot

**Note: HDA support not compiled in the driver (requires a 2.6.16 or later kernel)**

Ummm...

Nick

---

### Post by Linicks on 2007-11-15
OK, sort of **solved**.

If I revert back from kernel 2.6.22-14-generic to 2.6.20-16-generic then the driver builds and sound and modem work great.

So, this driver update doesn't build with kernel 2.6.22-14-generic.

What is the default kernel version for Gutsy 7.10 Ubuntu?

Nick

---

### Post by jdelaros1 on 2007-11-15
Linicks:

I have kernel 2.6.22-14-generic (default kernel for 7.10) but do *not* have backports installed. If you do, then that's probably what's breaking the driver. I don't think you need backports on 7.10 (it was on 7.04 to provide some fixes/workarounds) so remove backports and see what happens.

---

### Post by Linicks on 2007-11-15
> **jdelaros1 said:**
> Linicks:

I have kernel 2.6.22-14-generic (default kernel for 7.10) but do *not* have backports installed. If you do, then that's probably what's breaking the driver. I don't think you need backports on 7.10 (it was on 7.04 to provide some fixes/workarounds) so remove backports and see what happens.

Hey, hey, HEY!

Thank you, my friend, uninstalling backports has indeed FIXED the issue.  The new driver works fine now.

Thank you jdelaros1!

Nick

---

### Post by Linicks on 2007-11-16
Well!

It appears somebody @ Dell reads the reports here, as the Dell wiki ( read only for mortal users) has been updated:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver)

It would be nice if a Dell representative could acknowledge in the threads though, don't you think?  Otherwise it is all invisible.

Nick

---

### Post by neilius on 2007-11-18
...and I can also report that the 64 bit tarball works fine on Ubuntu 7.10 x86_64, just have to do the whole 'make install' thing with it. and run a config utility after. 64 bit Ubuntu never tasted so good on the 6400!

Rgds,

Neil.

---

