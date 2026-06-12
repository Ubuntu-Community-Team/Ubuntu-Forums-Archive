---
title: "keyboard layout shortcut"
date: 2009-08-16
forum: Desktop Environments
---

### Post by atri on 2009-08-16
I have to work with different keyboard layouts , the layout indicator is on the panel and a key defined to switch between layouts . But it would be more convenient to have a specific shortcut to get a specific layout , like e.g. Alt+F2 for English , Alt+F3 for Hindi etc. . Could anyone to help ?
Would it be possible to define a Custom Shortcut under System , Preferences , Keyboard Shortcuts ? But I would have to have a ‘ command ’ and I don’t know what that could be :-) .
Thanks for helping !

---

### Post by pterion on 2010-01-17
I am looking for the same answer. Please respond.

---

### Post by narr on 2010-01-17
You can switch layouts during a X-Server session using ```
setxkbmap layoutname
``` For a german layout for example: setxkbmap de
You need to bind this command to a key (add a shortcut). Press Alt+F2 and start: gnome-keybinding-properties 
In the new window click add, choose a name and set the command. Click ok. In the row which shows your command, click the right column and choose a shortcut.

---

### Post by DrunkElf on 2010-02-24
I had the same problem because i wanted to have two languages on my keyboard (Greek+English)... I use ubuntu 9.10...Firstly install the language pack and then System\Preferences\Keyboard\Layouts\Layout Options\Keys to change the Layout and choose alt+shift whch is familiar from windows(Damn Microsoft habbits!!! :P )... It solved my problem hope that helps you too...
:popcorn:

---

### Post by .Impact. on 2010-11-04
Thank you DrunkELf i managed to fix the problem ! Much love <3

---

### Post by hezuo on 2011-10-28
Thanks a lot, you made my day!

---

### Post by dimkatz on 2012-05-09
Many thanks!!! Very very useful tip!!!

---

