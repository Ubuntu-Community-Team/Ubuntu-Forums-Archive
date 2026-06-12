---
title: "[SOLVED] Dell Keyboard Screwup"
date: 2008-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by flummoxed on 2008-05-10
Hi,

I just installed ubuntu 8.04 on a Dell Optiplex GX520. Im using a Dell Multimedia USB keyboard, with the english Canada layout. Something weird is going on... For example, when I hit shift + 3, I should get the pound symbol, but instead I get the / symbol. All of the letters are working correctly, but the symbols are all out of whack. Does anyone have any idea what could be causing this

I would have put a question mark at the end of that sentence, but the question mark button makes É instead. Ive checked the keyboard menu in the preferences, as well as xorg.conf,  but everything seems to be fine.

thanks

---

### Post by flummoxed on 2008-05-11
NVM, I ran ```
sudo dpkg-reconfigure xserver-xorg
```, chose pc104 and us, and now it's working fine.

---

