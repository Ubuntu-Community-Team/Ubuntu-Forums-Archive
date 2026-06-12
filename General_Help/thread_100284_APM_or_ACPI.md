---
title: "APM or ACPI"
date: 2005-12-07
forum: General Help
---

### Post by ScreemingBlue on 2005-12-07
Does anybody know what the difference is between APM and ACPI, I think they serve the same function? Both are running on my box and I am sure if it is OK to turn one of them off, but which one?

Any ideas?

Cheers

---

### Post by ranf on 2005-12-07
APM is older. The kernel usually prefers ACPI over APM if both are available.
To find out what the kernel does type:
```

dmesg | grep -i acpi
dmesg | grep -i apm

```

---

### Post by arpunk on 2005-12-07
APM is known to cause certain problems, and ACPI replaces APM, so its ok to disable APM. Btw, i saw you have a radeon 9200, any problems with fglrx drivers? :(

---

### Post by ScreemingBlue on 2005-12-08
[QUOTE=ranf]APM is older. The kernel usually prefers ACPI over APM if both are available.
To find out what the kernel does type:
```

dmesg | grep -i acpi
dmesg | grep -i apm

```[/QUOTE]


Thanks for that, it seems my box likes using ACPI then. I shall turn APM off then.

---

### Post by ScreemingBlue on 2005-12-08
[QUOTE=arpunk]APM is known to cause certain problems, and ACPI replaces APM, so its ok to disable APM. Btw, i saw you have a radeon 9200, any problems with fglrx drivers? :([/QUOTE]

No probs using fglrx, I get out about 1850 fps using these drivers.

---

