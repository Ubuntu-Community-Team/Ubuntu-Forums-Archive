---
title: "What is a slashscreen?"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by mulle12 on 2008-03-23
As the title says: What is a splashscreen? When do they pop up?

Another question: Is there any way to NOT see the "grub loading, please wait" text when booting Ubuntu 7.10?

---

### Post by Ub1476 on 2008-03-23
There are two splash screens in Ubuntu: the one which you see when Ubuntu loads, and one which you can see (you have to enable it) when you log into your user account.

You can hide GRUB by editing /boot/grub/menu.lst (or installing a graphical front end for it), but I'm not sure if you can hide the "loading grub" text.. Probably possible in some way though.

EDIT: There's also a splash screen for Compiz-Fusion which you can enable in Advanced Desktop Effects/ccsm. And there is one for Open-Office as well. It's basically just an image which shows before the application has fully loaded.

---

### Post by mulle12 on 2008-03-23
> **Ub1476 said:**
> There are two splash screens in Ubuntu: the one which you see when Ubuntu loads, and one which you can see (you have to enable it) when you log into your user account.



The splashscreen that shows when i login, does that show when i press enter after typing in my password instead of some boring backgroundcolor?

Where/how do i enable it? Im new to Ubuntu.

---

### Post by durand on 2008-03-23
Ok, this is simple. In the terminal, type:

```

gconf-editor

```
Then click on Edit > Find and type in "show_splash_screen" without the quotes. Click on the first result. Now just tick the value column. See the screenshot below. You can change the splash screen by editing the value below it. There are loads of screens here: [http://gnome-look.org/index.php?xcontentmode=160&PHPSESSID=868e0beb747511dd069bd0acb9e56ea0](http://gnome-look.org/index.php?xcontentmode=160&PHPSESSID=868e0beb747511dd069bd0acb9e56ea0)

---

### Post by buntu_Geek on 2008-03-23
There is a simple GUI available for installing your own splash screen...

Its called Splash Screen

Its available in Add or Remove Applications..

just type Splash Screen on the top search bar... and install the appearing result... then you can find the app in System-->Preference-->Splash Screen

Then the gui is easy to use and are self explainatory..

---

