---
title: "How do you turn Compiz off?"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by Gizim on 2007-07-08
When i play WOW it doesnt play nice with the title bars any way to turn it off?

---

### Post by diegoruggeri on 2007-07-08
try run "metacity --replace"

---

### Post by Dyegov on 2007-07-08
I do it this way:

Alt + F2

Type: metacity --replace &

---

### Post by phssthpok on 2007-07-09
When running compiz, when I enter "metacity --replace &" my desktop locks up and I have to hard reset. Metacity usually gives me this error:

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager error: Unable to open X display

I'm running Feisty 7.04 and using the 100.14.11 nvidia drivers. I also have beryl installed and can activate metacity there without problems.

---

### Post by Espreon on 2007-07-09
Just use Beryl manager to activate Compiz and switch to Metacity/Beryl or whatever. What window decorator do you use? (i.e. Emerald, Heliodor, Compiz GTK decorator, Aquamarine)

---

### Post by phssthpok on 2007-07-11
i am using emerald. beryl-manager produces the same results: when trying to kill compiz.real, the computer hangs and only a hard reset will fix it. 

this only seems to happen when using indirect rendering to [partially] escape black windows.

i can kill compiz.real from a TTY without any trouble, but killing it from within X produces the above results.

---

