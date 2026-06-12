---
title: "apic error, how do I disable apic?"
date: 2006-10-03
forum: Desktop Environments
---

### Post by ewaguespack on 2006-10-03
this is showing up in my logwatch... looks like i may need to disable apic, does anyone know how to do it? i have googles and I see people suggesting apic=off, noapic, etc

imho, there should be one place to turn this off, and with a single command, does anyone know where / what that is?

thanks


 WARNING:  Kernel Errors Present
    [17219321.852000] APIC error on CPU0: 40(40) ...:  1 Time(s)
    [17253462.792000] APIC error on CPU0: 40(40) ...:  1 Time(s)
    [17263962.828000] APIC error on CPU0: 40(40) ...:  1 Time(s)
    [17267382.832000] APIC error on CPU0: 40(40) ...:  1 Time(s)
    [17269482.832000] APIC error on CPU0: 40(40) ...:  1 Time(s)
    [17269782.836000] APIC error on CPU0: 40(40) ...:  1 Time(s)

---

### Post by amohanty on 2006-10-03
If you are able to boot up normally, I would suggest just ignoring it.

To pass in noapic to the kernel during bootup, you will have to edit
**/boot/grub/menu.lst**

and add noapic at the end of:
**kernel          /vmlinuz-2.6.15-26-386 root=/dev/sdb5 ro single**

However, I would advise against it as it may cause delays in hdd access time. ALso be very, very careful about this, if at all possible just dont do it.

HTH
AM

---

