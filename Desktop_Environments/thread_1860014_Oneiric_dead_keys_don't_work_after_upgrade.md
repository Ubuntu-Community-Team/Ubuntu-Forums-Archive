---
title: "Oneiric: dead keys don't work after upgrade"
date: 2011-10-14
forum: Desktop Environments
---

### Post by Seb1982 on 2011-10-14
Hey Folks

I upgraded to Oneiric yesterday and noiced that my keyboard doesn't work as it should do.

I was using the US international keyboard layout with dead keys. That means that I was e. g. able the create the symbol á by typing ´ followed by a.

I tried the other international layouts and several options but the issue remains (in Unity as well as in Gnome 3).

Is it possible to reactivate dead keys?

Thank you!

---

### Post by Seb1982 on 2011-10-16
By the way: is it possible to change the login screen's language and input method? Maybe this is causing the problem.

---

### Post by riuri on 2011-10-18
Hello, Seb1982

I have had the same problem since I upgraded to Oneiric. I tried to change the language and the keyboard layout, but it did not solve the problem.

If you want to try, open the dash home (by pressing WinKey or Super), More Apps, Filter Results, Customization and Keyboard Layout or Language Support.

By the way, I could not write "Keyboard Layout" or "Language Support" on the dash home search. Did you face the same problem?

I also found strange that the sequence Ctrl+Shift+u and typing the unicode of one character does not work.

If I don't come to a solution, I might try to install Oneiric from the CD. The Natty installation setup had a screen where we could type some letters and it guessed what the keyboard layout was.

I hope it helps.

---

### Post by Seb1982 on 2011-10-21
Hey riuri,

nope, no issues with typing anything in the search field. Sorry :/

---

### Post by Seb1982 on 2011-10-21
Woohoo, I solved the problem!

The trick was to open the Language Settting and change the Input Method from "scim" to "Ibus".

---

### Post by JorritLin on 2011-11-05
ThatÂ´s really odd, dead-keys always worked fine without any IMEÂ´s installed.
Does not work with me, no matter if I use ibus, scim or any other imput method.
Canna and Anthy (Japanese IMEÂ´s) do not work either after the upgrade. I call this either a regression or a failure to note the differences in behaviour between 11.04 and 11.10 by the Ubuntu documentation team.

---

