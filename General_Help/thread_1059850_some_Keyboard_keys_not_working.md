---
title: "some Keyboard keys not working"
date: 2009-02-04
forum: General Help
---

### Post by mosty friedman on 2009-02-04
hey everyone,
i have a problem with my keyboard, before it was working fine but starting from yesterday some keys stopped to work on ubuntu 8.10 eventhough everything works fine on vista, what could be the problem???

---

### Post by utnubuuser on 2009-02-04
Hi -- Maybe xorg got corrupted somehow?
try running > sudo dpkg-reconfigure xserver-xorgin a terminal.

---

### Post by mosty friedman on 2009-02-05
thanks for the reply, i tried what you said but it unfortunately didnt work :(

---

### Post by mosty friedman on 2009-02-06
please people, i need help with this...the thing is the plus/equal as well as the dash/underscore keys arent working, and i really need them for my programming..

---

### Post by utnubuuser on 2009-02-06
Well...  wasn't there a kernel upgrade recently? Maybe your keyboard has an issue with the new kernel.  have you checked any of the threads about using the previous version of the kernel?  again, just a suggestion.

You say you tried the xserver-xorg reconfiguration and it did nothing to help, even with a different configuration setting?  What I mean is there are several options when you're going through the reconfiguration process.
Is it a special keyboard? ie. a media-keyboard?  There are how-tos on configuring media-keyboards.
Sorry if I seem to be going on a bit here, considering that this board worked until recently.
When you boot the machine, at the grub-loader, are your older kernels listed, and have you tried using one of these?  Have you checked the board in rescue-mode?

---

### Post by mosty friedman on 2009-02-06
its not a special keyboard, its a normal laptop keyboard and it was working fine with 8.04 and 8.10 until about 4 days ago, some keys stopped working..i have been googling around to find a solution but couldnt find anything.

---

