---
title: "kernel issues with eee901"
date: 2009-02-13
forum: General Help
---

### Post by relic12345 on 2009-02-13
Hi,

I have just installed unbuntu on my eee901 and am having some difficulties.  I used the array.org kernel so i could get wifi working.  the problem i am having is that to load up that kernel i have to press esc everytime i turn on the computer else it will just load up the standard kernel.

how do i sort this out?

thanks

Colin

---

### Post by Yellow Pasque on 2009-02-13
Can you post your /boot/grub/menu.lst?
You just need to change the 'default' line, but it's a bit tedious/complicated to explain.

---

### Post by relic12345 on 2009-02-14
reinstalled it and used the option to remove updating of generic kernel - thats what caused the problem as update ran on first instal land mucked it up.

---

