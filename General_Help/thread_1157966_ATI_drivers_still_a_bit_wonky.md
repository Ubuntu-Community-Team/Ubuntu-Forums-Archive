---
title: "ATI drivers still a bit wonky?"
date: 2009-05-13
forum: General Help
---

### Post by NoPantsJim on 2009-05-13
I'm installing Ubuntu on an older machine that I haven't used in almost a year, but having problems with the ATI drivers. I'm running a radeon 1650 and outputting it with DVI to a 42" lcd at 1920 x 1080. When I do the mandatory restart after installing the drivers, I get all the normal Asus load screens from my motherboard, and the Ubuntu load screen, but when it switches over to where the login screen should be, it goes 100% black. The computer will remain in this state for hours. Attempting to switch to one of the virtual terminals (not sure if that's the right name?) does nothing. Here's the odd thing though, it is definitely sending a signal, as my hdtv will turn itself off if it is turned to a DVI input that is not sending a signal. Any ideas?

Thanks.

---

### Post by Legace on 2009-05-13
Did you install the closed source (FGLRX) drivers? They don't support your card anymore [if you use Jaunty].

---

### Post by NoPantsJim on 2009-05-13
I'm installing off of a 8.04 disk. I'm not sure of the name of the drivers, but they are the ones that Ubuntu automatically prompts you to download after initially installing the OS.

---

### Post by Dimarchi on 2009-05-14
Did you do sudo aticonfig --initial -f after you had installed the prompted driver? Can be done in console afterwards. It may help.

---

