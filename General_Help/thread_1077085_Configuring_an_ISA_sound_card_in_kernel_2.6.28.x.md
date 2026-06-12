---
title: "Configuring an ISA sound card in kernel 2.6.28.x"
date: 2009-02-22
forum: General Help
---

### Post by K.Mandla on 2009-02-22
This is a bit of a long shot, but I'm trying to configure an ISA sound card with the 2.6.28 kernel. Of course I'm not having any luck. ;)

Ordinarily with PCI audio cards I simply enable the ALSA subsystem and the appropriate hardware support. This card is supposedly Soundblaster Pro compatible, but the kernel shows no associated hardware on boot, and alsaconf can't find anything soundwise.

I've tinkered with a few other modules but usually get similar, if not the same, results. I have tried both modular and built-in support for SB Pro, but neither seems to work. 

Do ISA cards require a different procedure to get the kernel to detect the hardware? Does ISA hardware rely on any other part of the kernel that I might have disabled (I have been known to attack kernel configuration with a little too much enthusiasm)?

For the record, [this is the machine]("http://kmandla.wordpress.com/hardware#FMV-5100"), and [this is supposedly the guts]("http://translate.google.com/translate?prev=hp&hl=en&u=http%3A%2F%2Fpr.fujitsu.com%2Fjp%2Fnews%2F1996%2FMay%2Fnushiyou.html&sl=ja&tl=en").

P.S.: I tagged this "Other OS" because it's running Crux, but that's not necessarily the only distro that would apply.

---

### Post by geraldm on 2009-02-22
ISA bus is sometimes behind a bridge, and this may be harder to find.
Some ISA cards were Plug & Play.  This has been removed from the kernel.
If it is detected it would show up in subdirectories of /sys/bus/isa/   ?
There is some information in the kernel source file Documentation/pnp.txt

best regards,
Gerald

---

### Post by K.Mandla on 2009-02-25
> **geraldm said:**
> ISA bus is sometimes behind a bridge, and this may be harder to find.
Some ISA cards were Plug & Play.  This has been removed from the kernel.
If it is detected it would show up in subdirectories of /sys/bus/isa/   ?
There is some information in the kernel source file Documentation/pnp.txt

best regards,
Gerald
Thanks, Gerald. I'll give this a try. I'm not sure it's worth pursuing but it would be one more little thing I could check off my to-do list. :)

---

