---
title: "Changing the login screen on Ubuntu"
date: 2011-10-07
forum: Desktop Environments
---

### Post by MCcloud.dk on 2011-10-07
Hi

I am still new to Ubuntu and i was wondering if it was possible to change the Login screen on startup, if so how?

---

### Post by Krytarik on 2011-10-07
Well, depends on what display manager you are using ;-) :

[LIST]
[*]GDM (default up to Natty 11.04): [http://www.tuxgarage.com/2011/05/customize-gdm-plymouth-grub2.html](http://www.tuxgarage.com/2011/05/customize-gdm-plymouth-grub2.html)
[/LIST]
[LIST]
[*]LightDM (default from Oneiric 11.10 on): [http://www.tuxgarage.com/2011/10/customizing-appearance-of-lightdm.html](http://www.tuxgarage.com/2011/10/customizing-appearance-of-lightdm.html)
[/LIST]
Regards.

---

### Post by MCcloud.dk on 2011-10-07
Okay well i am using Natty Narwhal 11.04, but if i use the one tutorial you recommend, is it reversible to the original login screen if i screw things up?

---

### Post by Krytarik on 2011-10-07
> **MCcloud.dk said:**
> Okay well i am using Natty Narwhal 11.04, but if i use the one tutorial you recommend, is it reversible to the original login screen if i screw things up?
Sure, personally, I'd just keep the original settings in mind or write them down, so I could easily change them back. Otherwise, you'd need to use "gconf-editor" (or "gconftool-2" for that matter) to 'unset' the respective keys, which are not exactly in one place :P , and thus a bit tricky to find.

---

