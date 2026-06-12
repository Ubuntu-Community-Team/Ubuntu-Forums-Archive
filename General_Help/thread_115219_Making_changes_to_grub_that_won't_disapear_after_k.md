---
title: "Making changes to grub that won't disapear after kernel upgrade/change"
date: 2006-01-10
forum: General Help
---

### Post by encompass on 2006-01-10
How do I keep my changes to grub menu.lst permenently rather than losing those changes when I upgrade my kernel?  I had this problem with debian, the told me once... but I have forgotten.  Thanks for the help.:)

---

### Post by lorenco on 2006-01-10
You may add some options  before or after this section ?:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below


What options are you looking for ?

---

### Post by encompass on 2006-01-10
I like to set the console display detail to 1024x768 so I can 'see' more in my console work... so I set that to vga=0x318 great thing for me... but when grub is updated with apt-get it destroys the changes.

---

