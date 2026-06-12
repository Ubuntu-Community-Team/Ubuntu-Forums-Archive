---
title: "Can i add a custom message to the grub boot menu"
date: 2009-05-05
forum: General Help
---

### Post by thingy87654321 on 2009-05-05
can i add a custom message to the grub boot menu? i want to add this message



33424 custom system
BY: Chris Aouate

---

### Post by kellemes on 2009-05-05
> **thingy87654321 said:**
> can i add a custom message to the grub boot menu? i want to add this message



33424 custom system
BY: Chris Aouate

Edit /boot/grub/menu.lst
And change the title of one of your boot-entries.. just the title.
Or isn't this what you mean?

---

### Post by thingy87654321 on 2009-05-05
no, i know how to change that, i want to add a little message on the grub bootloader menu, if that is possible. is it possible?

---

### Post by Vaphell on 2009-05-05
you mean you'd like to add some lines with messages?
I have something like that in my menu.lst:

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

so title is shown message - it is selectable, but nothing will boot from it
I guess you can add your message in such way: define title and not define root

---

### Post by thingy87654321 on 2009-05-05
thats perfect

---

### Post by sir_nasty on 2009-05-05
with a bit of research you could create a custom splash image that would contain that text as part of it and be a background....

---

### Post by thingy87654321 on 2009-05-05
if you would like to make me one, go ahead

---

