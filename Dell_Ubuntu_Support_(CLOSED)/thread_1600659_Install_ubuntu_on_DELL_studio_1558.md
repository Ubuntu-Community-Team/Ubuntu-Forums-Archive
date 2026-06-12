---
title: "Install ubuntu on DELL studio 1558"
date: 2010-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fuloperformer on 2010-10-19
Good Morning; i just want to install ubuntu 9.10 on a DELL studio 1558, i have the original yellow cd, and i can only see the main menu where i can boot into the live cd, and install ubuntu, and when i try to install it, the screen gets black and it cannot install, but the optical drive makes noise that cd is spinning, when i install it inside windows, the same issue, black screen and it does not works

do i need to change any setting on bios or to install any upgrade on bios?

---

### Post by gibbylinks on 2010-10-19
Probably need to add "nomodeset" to the grub line. 

Hold down shift to enter grub menu, then "e" to edit the line and add the word "nomodeset" after "quiete splash"

Afterwards you'll need to update grub so that it does it every time.

---

### Post by fuloperformer on 2010-10-19
in the grub i need to press shift?

---

### Post by fuloperformer on 2010-10-19
> **gibbylinks said:**
> Probably need to add "nomodeset" to the grub line. 

Hold down shift to enter grub menu, then "e" to edit the line and add the word "nomodeset" after "quiete splash"

Afterwards you'll need to update grub so that it does it every time.

I performed the steps, added nomodeset on the grub and same issue, black screen after ubuntu started, but the curious thing is that i out another hdd with ubuntu installed and it booted correctly.

---

### Post by fuloperformer on 2010-10-20
i tried fedora 64 bits and it worked fine, so i will download the ubuntu 64bits to check if it works fine

---

