---
title: "Weird behavior with quote key in ubuntu 8.04"
date: 2009-02-24
forum: General Help
---

### Post by y17chen on 2009-02-24
Hi 

I am running Ubuntu 8.04 in VMplayer and came across a very strange problem. It seems that I have a hard time pressing the "quote" key on my keyboard while in Ubuntu 8.04. The weird behavior are: pressing the quote key once nothing happends, pressing it again a dot appear as oppose to a normal single quotes: '. Pressing shift+quote key, again first time nothing shows up, second time two dots appear as oppose to the normal double quote: ". This is a problem because then java compiler is not able to recognize this 'two dot' operation and throws errors. 

If anyone have seen this problem and know what is wrong please help! There is nothing wrong with my keyboard thou, it worked fine with normal typing in windows. 

Please help! Thank you
-y

---

### Post by geraldm on 2009-02-24
The US keyboard has no dead keys.
The US_International keyboard layout has dead keys and " is one of them.

[http://en.wikipedia.org/wiki/Keyboard_layout#Dead_key](http://en.wikipedia.org/wiki/Keyboard_layout#Dead_key)

To get the " key to work on the first keypress, you would have to choose a
layout that does that. The US keyboard releases it on the first keypress.
The US_International layout does not release on the first keypress, but releases after the subsequent keypress.  The dead keys are those that carry an accent type.  With the subsequent keypress, (usually a vowel) the properly accented vowel keypress is released.

Gerald

---

