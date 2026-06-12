---
title: "Since update, keyboard layout problem"
date: 2005-12-05
forum: Desktop Environments
---

### Post by haldrik on 2005-12-05
Hello Everyone:
I installed 5.1 with no problems and was using an international keyboard layout (w deadkeys) exclusively. After a week or so, I did the mega-update of all updated packages. After doing so, I have two major problems:
1. The international keyboard doesn't work. I've tried changing the setting in /etc/X11/xorg.conf ("Option	"XkbLayout"	"us-intl") as well as removing the US keyboard in GNOME and replacing it with the International keyboard. No matter what I do, I still only have the regular American keyboard layout with no dead-keys for making accented characters.
2. GNOME starts with an unknown error:
"There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The Settings Daemon restarted too many times.
The last error message was:
Child process did not give an error message, unknown failure occurred
GNOME will still try to restart the Settings Daemon next time you log in." 

One of the quirks of this error is that all icons on the the bottom panel are just a red X in a box.

Anyone know how I can get my INTL keyboard back? (I need to have a compose key as well, such as right-alt in order to make the German ' ß '  letter.)

Thanks for any help! I'm a German teacher and am in trouble if I can't make German letters!

---

### Post by haldrik on 2005-12-05
Based on another users question, I also tried the following command:
dpkg-reconfigure xserver-xorg and there putting us-intl as keyboard.
This had no effect on the situation.

Any help greatly appreciated!

---

### Post by EstevaoSoares on 2006-02-08
Hi there folks... 


Same problem with me... 

I'm in a Compaq Presario v2000.

Thx in advance.

---

### Post by viciouslime on 2006-04-22
[QUOTE=haldrik]Hello Everyone:
I installed 5.1 with no problems and was using an international keyboard layout (w deadkeys) exclusively. After a week or so, I did the mega-update of all updated packages. After doing so, I have two major problems:
1. The international keyboard doesn't work. I've tried changing the setting in /etc/X11/xorg.conf ("Option	"XkbLayout"	"us-intl") as well as removing the US keyboard in GNOME and replacing it with the International keyboard. No matter what I do, I still only have the regular American keyboard layout with no dead-keys for making accented characters.
2. GNOME starts with an unknown error:
"There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The Settings Daemon restarted too many times.
The last error message was:
Child process did not give an error message, unknown failure occurred
GNOME will still try to restart the Settings Daemon next time you log in." 

One of the quirks of this error is that all icons on the the bottom panel are just a red X in a box.

Anyone know how I can get my INTL keyboard back? (I need to have a compose key as well, such as right-alt in order to make the German ' ß '  letter.)

Thanks for any help! I'm a German teacher and am in trouble if I can't make German letters![/QUOTE]

I have this exact same problem, maybe its a bug?

If i try to change my keyboard layout, or add a compose key as soon as i tick the box gnome starts changing theme elements rapidly back and forth between the theme i have selected and some other theme. I start getting LOTS of warnings about icons being missing and then if i reboot i get a message about the gnome settings daemon not being ables to start.

Anyone know how to fix this? i too really need to be able to type acented characters on my keyboard. Please help!

---

### Post by viciouslime on 2006-04-22
Surely there is a solution to this? Typing in more than one language on only one keyboard is essential for many people.

---

