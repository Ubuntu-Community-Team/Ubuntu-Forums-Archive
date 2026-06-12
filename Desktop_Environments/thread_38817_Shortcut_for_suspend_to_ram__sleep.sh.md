---
title: "Shortcut for suspend to ram / sleep.sh"
date: 2005-06-02
forum: Desktop Environments
---

### Post by RAF on 2005-06-02
Hi,

I made suspend to ram work on my Laptop (Acer Travelmate800Lci) recently, but I can only activate it by running the sleep.sh in the console in /etc/acpi/ or via the logout screen. Both possibilties are not very handy.

First I thought of getting my FN-Keys working. But it seems this won't be easy.

Second I thought of replacing the lid.sh with the sleep.sh to activate it when the lid gets closed - well, then I recognized the lid.sh is not started when the lid is closed, so this won't solve the problem.

Third I thought of starting the sleep.sh with an button in the panel. This works but I have to start it with sudo from there, so it needs the password!

Now I have no more ideas. Could someone please help me?

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=RAF]Hi,


Second I thought of replacing the lid.sh with the sleep.sh to activate it when the lid gets closed - well, then I recognized the lid.sh is not started when the lid is closed, so this won't solve the problem.
[/QUOTE]

It is supposed to - at least, this is the way I did for my laptop (Dell Latitude). Does the ACPI log registers lid closing event?

---

