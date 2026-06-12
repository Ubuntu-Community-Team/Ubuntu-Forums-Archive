---
title: "Reducing acpi output"
date: 2009-06-08
forum: General Help
---

### Post by Jaded Misanthrope on 2009-06-08
I'm setting up Conky on my Ubuntu 8.10 installation, and so far it's been going rather well except for one thing: battery status.

None of the inbuilt variables for Conky work to show my battery status, so instead I'm using ${execi 1 acpi}, which places the output of acpi into the display. However, I find that the output is far too verbose: all I need is a percentage, not
```
jack@Sputnik:~$ acpi -b
Battery 0: Discharging, 92%, discharging at zero rate - will never fully discharge.

```

To use the above example, is there a way to have the output just be 92% (or even just 92)? I also need to reduce the output of acpi -a -B from 'AC Adapter 0: online / offline' to just 'online' or 'offline', but I'd assume that whatever technique was used to reduce output for the first command would work just as well here.

---

