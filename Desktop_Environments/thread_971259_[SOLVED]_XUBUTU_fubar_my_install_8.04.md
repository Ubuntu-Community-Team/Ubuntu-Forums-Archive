---
title: "[SOLVED] XUBUTU fubar my install 8.04"
date: 2008-11-04
forum: Desktop Environments
---

### Post by lenswipe on 2008-11-04
As the title says the following no longer work properly if at all:

terminal: works and runs but when tpying anything behind the cursor is invisible.

compiz: does not work at all - neither does the advanced desktop effects found under the Desktop Settings dialog box

AWN: Does not work at all

Also for some strange reason when i login it shows me a tty terminal tty2 to be exact then i get a series of thin green lines covering the entire top 10th of the screen.

It would apear that contrary to all popular belief you cannot run multiple desktop environments on the same machine at once. It works with centos, but not with ubuntu for some reason.

Anyone know how i can fix the forementioned problem?

I have run sudo aptitude remove xubuntu-desktop. However the problem still exists. Can anyone help me into getting my computer back the way it was before Xorg f***** it up?

If i run the command ```
glxinfo | head
```

also my keyboard has swapped itself to an american layout for some unknown reason too..
Thanks

-L

---

### Post by lenswipe on 2008-11-05
nvm people after being powered off for 24 hours and running the command:

sudo apt-get remove xubunt-desktop.

My laptop seems to have sorted itself out -.-


Just take note from this people and dont run 2 window managers at once.

---

