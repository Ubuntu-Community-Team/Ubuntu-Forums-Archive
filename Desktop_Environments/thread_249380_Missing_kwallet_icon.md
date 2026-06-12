---
title: "Missing kwallet icon?"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Revan on 2006-09-02
Hi guys,

I have a few problems with my Kubuntu 6.06 that really annoy me.

1. Though Kopete is prompting for the kdewallet password everytime I start the program, the kwallet icon never shows up on my tray. I'd like to change the wallet password, but without that icon I don't really know how to do it :(

2. I've recently upgraded to KDE 3.5.4, but my screensaver is still broken: it doesn't lock the session when it starts, so it doesn't require any password when I come back to my PC. I read that this was a 3.5.3 bug and that it was fixed with 3.5.4, but it didn't change at all on my system :-|

3. I'm a victim of the "Will Now Halt" bug, my PC doesn't shut down automatically and locks on the "Will Now Halt" line. I've tried modifying GRUB with the acpi options, but never solved this problem. Should I try compiling a custom kernel?

I have an Asus P5GD2 Premium motherboard with an Intel P4.

---

### Post by danko on 2006-09-06
I have the same problem regarding missing kwalletmanager icon. I found related bug report No 129161 for version 3.5.3 on KDE site, but it is marked as resolved. As workaround that will enable you to change wallet password, you can kill kwalletmanager process from the terminal window, and restart it again. This way, wallet icon will appear at desktop.

---

### Post by jpmorelli on 2006-09-14
Work for meee, thanks !!!

Also you can run:
kwalletmanager --show

:KS

---

### Post by carla on 2006-12-26
> **jmorelli said:**
> 
Also you can run:
kwalletmanager --show


When I did the above (in Edgy), the response was
```
ERROR: KUniqueApplication: Can't determine DISPLAY. Aborting.
```

Any suggestions?

---

