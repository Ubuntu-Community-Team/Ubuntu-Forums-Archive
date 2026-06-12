---
title: "Won't shutdown properly? Blank screen, hardware stays on."
date: 2009-05-30
forum: General Help
---

### Post by thecheeks on 2009-05-30
So no matter what method I use (command line, Gnome Shutdown), Ubuntu will shutdown to a blank screen, but will never shutdown the hardware. I saw a solution where you add ampower=1 or something like that to /etc/modules but that didn't work either...

---

### Post by spiderbatdad on 2009-05-30
Are you using any special boot options like acpi=off? It may be that the option apm=off will help...not entirely sure. your dmesg log might help you. In any event, it is safe to shut down with the power button once the system has halted...though it is inconvenient.

---

### Post by thecheeks on 2009-05-30
> **spiderbatdad said:**
> Are you using any special boot options like acpi=off? It may be that the option apm=off will help...not entirely sure. your dmesg log might help you. In any event, it is safe to shut down with the power button once the system has halted...though it is inconvenient.

Where do I find this information? My linux knowledge is pretty spotty still.

The bad part about using the power button is it makes my HFS+ drive think there was a power failure or something and it will become read only when I start the computer again, unless I hook it back up to my mac and verify it.

I've tried a LOT of fsck tutorials for getting it to work with HFS+ non journaled, but I think the problem is is that it was formatted with OS X and the problem lies with the OS9 drivers installed to it when formatting. Something like that... ugh.

Edit: Installed latest ATI drivers and it now shutdown properly. No idea why that would fix it....

---

