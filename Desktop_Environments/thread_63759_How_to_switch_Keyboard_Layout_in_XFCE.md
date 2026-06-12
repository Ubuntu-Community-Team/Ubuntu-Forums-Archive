---
title: "How to switch Keyboard Layout in XFCE?"
date: 2005-09-08
forum: Desktop Environments
---

### Post by kagashe on 2005-09-08
Hi,

I have already set up Hindi keyboard layout in gnome which was very easy. I have added the layout switcher to the gnome panel which is working well.

Now my problem is to creat this in XFCE.
I have checked the Keyboard Settings option in XFCE but there is no way to add another keyboard layout. It seems XFCE is lagging behind gnome in this feature.
I have added the layout switcher to XFCE panel but it is showing only the default keyboard and not showing the Hindi keyboard. 

I tried setxkbmap dev command and the layout changed to Hindi but I could not switch back to the default layout since I could not type the command in English.

It seems it is necessary to fiddle with xconfig files to add the Hindi keyboard layout to the layout switcher in XFCE and I am not very proficient to do that.

Guidance please.

kagashe

---

### Post by varunus on 2005-09-09
A temporary fix; you could always run a gnome panel in XFCE instead of the XFCE panel.  But that's short term.

I'm not sure how to change keyboard layouts...GNOME is far ahead of XFCE in features because XFCE is designed to be much more lightweight.

You could try running GNOME with xfwm4 as the window manager; this will run faster.  Are you running XFCE because the computer is slow?  Running xfwm4 will speed it up a lot...even in GNOME.

---

### Post by kagashe on 2005-09-09
[QUOTE=varunus]A temporary fix; you could always run a gnome panel in XFCE instead of the XFCE panel.  But that's short term.

I'm not sure how to change keyboard layouts...GNOME is far ahead of XFCE in features because XFCE is designed to be much more lightweight.

You could try running GNOME with xfwm4 as the window manager; this will run faster.  Are you running XFCE because the computer is slow?  Running xfwm4 will speed it up a lot...even in GNOME.[/QUOTE]
 Yes, I run XFCE because I have 128 MB RAM and XFCE boots very fast also the applications open slightly quicker.
How to run gnome panel in XFCE?
How to run gnome with xfwm4?

kagashe

---

### Post by kagashe on 2005-09-16
Hi,
I received the information on XFCE Wiki:
> Add the XkbLayout Option to your xorg.conf-file. Here is an example if you want to use german and russian keyboard-settings:

   Section "InputDevice"
   Identifier  "Keyboard0"
   Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "de,ru"
   EndSection
In the last line I used > Option      "XkbLayout" "us, dev"since I use English (US) and Devanagari (dev) keyboard.

Meanwhile I have also learned to replace metacity by xfce window manager in gnome and run gnome desktop in XFCE.

kagashe

---

### Post by arazaxirelcinellersadolur on 2005-12-13
i understand that by this way we can "input" by these two keyboard layouts, wichone goes; BUT TWO.
i want to know: if i type at that ...conf. file smt. like that:

 Option "XkbLayout" "us,tr,ar"

will it run or no?
best regards

---

