---
title: "Intel HD 4000 support and brightness toggle."
date: 2013-05-02
forum: Desktop Environments
---

### Post by t430 on 2013-05-02
Hi,

I am running Ubuntu 12.04 on my personal laptop (T430 with 16 GB RAM, Intel HD 4000[No Nvidia switchable graphics]).

Tried 13.04 and it really looks awesome. Found that brightness toggling does not work with the Function Keys, but I can toggle brightness using the slide bar.

I had tried Beta 2 a couple days ago, found the same issue, reported it here, and the ever helpful folks here had helped so I can use the same tweaks, but I will be thankful if someone can tell me:

1) Does it appear that this issue will be fixed through patches that will be released in coming days ?

2) Does 13.04 fully support Intel HD 4000 driver? It shows up something like "intel graphics" driver in the "Graphics" section under settings, but doesn't specifically say anything about HD 4000. Is there some command that I can run to check it?

Kindly let me know.

---

### Post by screaminj3sus on 2013-05-02
1. this isn't really an intel problem, but an kernel/acpi problem. I've done a quick bit of research and it seems to be caused by a regression in kernel 3.8 (bug link: [https://bugzilla.kernel.org/show_bug.cgi?id=51231](https://bugzilla.kernel.org/show_bug.cgi?id=51231)). From what I can see it can be easily worked around by doing the following:

[B]sudo nano /etc/default/grub
[/B]
add **acpi_osi="!Windows 2012"** to the line that says **GRUB_CMDLINE_LINUX_DEFAULT=**, it should look something like this: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="!Windows 2012""**

Then save the file with ctrl + o and run **sudo update-grub** and reboot. It will probably be fixed in a future kernel, but I have no idea if it will ever be fixed for 13.04's kernel. the workaround should work anyway :)

2. 13.04 has excellent support for HD4000 graphics. afiak the vague info in system settings is due to ubuntu missing a package by default. If you install the "**mesa-utils**" package you should see more detail when you go into system settings > details. :)

---

### Post by t430 on 2013-05-02
Hi  screaminj3sus,

Thank you very much for such a detailed reply.

Everhelful community is one of the biggest strong points of Ubuntu, this is why there are so many ubuntu users :)

---

