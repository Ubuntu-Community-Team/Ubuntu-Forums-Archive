---
title: "thinkpad x61 troubles"
date: 2009-01-20
forum: General Help
---

### Post by dverg on 2009-01-20
Hello.

I am in the process of installing ubuntu 8.10 (amd64) on my lenovo x61 tablet.

I have some problems i cannot find the solution for on my own, help would be appreciated.

I cannot disable my bluetooth. I have found a workaround that involves adding this line to /etc/modprobe.d/thinkpad_acpi.modprobe

"options thinkpad_acpi experimental=1 hotkey=enable,0xffff8f bluetooth=disable"

the problem is that i cannot find this file in /etc/modprobe.c, but i find the file toshiba_acpi.modprobe

Could this be the source of my problems? I also have problems with many of the funktion-keys on my keyboard not working. Have ubuntu detected the wrong hardware? Is there a way to fix this?

Thank you for any help.

Best regards.

---

### Post by dverg on 2009-01-20
let me rephrase: how do I install thinkpad_acpi.modprobe and remove the toshiba_acpi.modprobe?

i am quite green on linux...

thanks again.

---

