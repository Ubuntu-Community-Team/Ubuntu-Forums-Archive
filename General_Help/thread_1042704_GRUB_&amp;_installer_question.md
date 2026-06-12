---
title: "GRUB &amp; installer question"
date: 2009-01-17
forum: General Help
---

### Post by quonsar on 2009-01-17
I have 8.10 installed, and would like to install the 64-bit version onto a second partition. If I allow the installer to install grub on my original partition, will it preserve my current grub setup? I realize I can just tell it not to install a boot manager and then edit my existing menu.lst by hand, but then I assume I would have to edit every time kernel upgrades happen. Is there a way for update-grub to manage more than one partition?

---

### Post by caljohnsmith on 2009-01-17
I would suggest installing Grub to the boot sector of your 64-bit new installation, not your original installation. Then in your original installation you can boot the new installation with:
```
title Ubuntu 64-bit Grub menu
root (hdX,Y)
chainloader +1

```
And replace (hdX,Y) with the 64-bit installation partition. Then whenever you get kernel upgrades in the 64-bit install, it's menu.lst will be updated, and you will see the change on start up since you are just booting the 64-bit install from your original install. Good luck and let me know how it goes or if you run into problems.

---

### Post by quonsar on 2009-01-17
Awesome! That's the functionality I was hoping for! (Coincidentally, I was JUST reading about chainloader in the grub docs.) Will set it up and let you know!

---

### Post by quonsar on 2009-01-18
Thank you caljohnsmith! This works perfectly now, and if I add other distros in the future I'll know what to do :):popcorn::guitar:

---

### Post by caljohnsmith on 2009-01-18
Glad to hear that worked OK; cheers and enjoy Ubuntu and any other distros you decide to try. :)

---

