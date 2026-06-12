---
title: "Login menu user selector"
date: 2006-01-12
forum: General Help
---

### Post by Mazin on 2006-01-12
How do I get a menu of users at the login screen, a la winxp home?

---

### Post by dgold on 2006-01-13
[QUOTE=Mazin]How do I get a menu of users at the login screen, a la winxp home?[/QUOTE]
I presume you are using gdm, the default login magaer with ubuntu.

From you Gnome desktop, choose menus as follows: 
System -> Administration -> Login Screen Setup
You will need to enter your password as this is a root operation.

Again, presuming a default setup, you will want to click on the 'Themed Greeter' tab of the setup window.

The only default option for a menu iof users, a la WinXP, is callled 'Happy Gnome with browser'. Click the radio button next to this, you should see a preview in the theme browser. Then just hit the 'Close' button to exit the setup screen normally.

The next time you start up, you will see a menu of users. Note also that each user can change their 'photo' displayed using 
System -> Preferences -> Login Photo

There are more themed greeters available on gnome-look.org, look for the section 'GDM Themes' in the options list on the left hand side of the screen.
HTH HAND

dgold

---

### Post by metoo on 2006-01-13
If you use kdm:
- open a console
- kdesu kcontrol   (or sudo kcontrol)
- provide (user) password (you need to be in the sudoer group, needs root rights)
- system administration - boot manager (guessing, de settings here)
- tab user
- check box at 'user - show list' (or similar, guessing again)
- hit apply button

---

### Post by Mazin on 2006-01-13
I don't know why, but Kubuntu must be using its own login screen because none of my settings do anything.  Things like using a clock instead of a logo, greeting text, user list, etc. are totally ignored by the (ugly) Kubuntu login menu.  I'm guessing it's a Kubuntu customization of KDE, but I want it gone and to use my settings instead.  How?

---

### Post by mattie on 2006-01-14
i had to disable theming in order to get a user list...
just disable it in /etc/kde3/kdm/kdmrc

> UseTheme=false

hth
mattie

---

