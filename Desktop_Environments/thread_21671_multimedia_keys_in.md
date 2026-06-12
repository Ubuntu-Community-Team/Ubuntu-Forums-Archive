---
title: "multimedia keys in"
date: 2005-03-23
forum: Desktop Environments
---

### Post by smtanner on 2005-03-23
I just installed kubuntu from a ubuntu installation and am having trouble mapping the volume button with kmix.  Under gnome it was easy but I can't get kmix to recognize the button.  I tried right clicking the slider in kmix and choosing configure shortcuts but hitting the volume button produces nothing.

---

### Post by techlord on 2005-03-23
i had a similar problem and made an Xmodmap file in /etc/X11/ and then in my kde/Autostart/ wrote a little shell script to call the xmodmap.

---

### Post by haggai on 2005-03-23
Control panel -> regional -> keyboard layout -> keyboard model

Make sure you have selected your keyboard from the list - otherwise the keys will not be recognised

---

### Post by smtanner on 2005-03-23
It is a notebook keyboard (gateway m675) and I do not see it in the list.  I did not have to select a keyboard in gnome for the keys to be recognized.  Maybe that is the problem, would it work to just select for instance microsoft multimedia keyboard?

---

### Post by misterlizard on 2005-03-27
I have an unbranded multimedia keyboard (with 15 extra keys on the top). I had to set it to 'Microsoft Internet Keyboard' under
Control panel -> regional -> keyboard layout -> keyboard model
for the keys to be recognised, it was on 'Generic 102 key (intl) PC' layout before.

It's probably worth trying the 'Microsoft Internet Keyboard' layout if you've already got it working with the Generic layout. If it does go wrong you should still be able to use the keyboard OK outside of X.

---

### Post by smtanner on 2005-03-27
thanks, that worked.

---

