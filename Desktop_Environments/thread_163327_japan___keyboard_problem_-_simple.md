---
title: "japan ?  keyboard problem - simple ?"
date: 2006-04-20
forum: Desktop Environments
---

### Post by dotdot on 2006-04-20
before anyone tells me - in know i've posted this under 
"keyboard" a couple of days ago.

Does anyone have a japanese keyboard running ubuntu in english that works ?
(how did you do it - ...?)

there you go can't make it any simpler.

.. i have a jvc mini note book... model   mp  xp 7310
everything works apart from a few crucial key strokes - pipe being one of them...

can anyone help.. ?

else - how do i pay for a result on this.. ?

jvc have been useless so far - both uk and us support people.

oh and in case you're intersted.. windows works fine - which in this case is doubley disturbing...

...tia

---

### Post by dmizer on 2006-04-20
i have a japanese laptop with a japanese keyboard.

when you set up your keyboard, do not set it up as english, set it up as japanese.  the japanese type in english characters as well, so you won't end up with hiragana all the time if you install your keyboard as japanese instead of english.

the problem is that if you set your keyboard as english, there are several "unknown" keys that ubuntu will not know what to do with and cause you problems.  but if you set it up as japanese, then they keys are recognized and the keyboard will work.

though you'll end up with other small annoyances like having to type <shift>+7 to get an apostrophy and <shift>+2 to get a quote ... but you'll get use to it.

---

### Post by dotdot on 2006-04-24
problem partly solved.

get a hold of xmodmap from synaptic.

Trashed all setting - panic'ed - thought the only way out was reinstall... then 
miraculously got xmodmap back up - then reset to default - brought me a pipe !

pipe - yes pipe was the source of all my problems ...

...thanks for all adv on this issue.

btw if you ever use xmodmap - be VERY VERY CAREFUL.

..

---

### Post by fonggiding on 2006-04-25
I am using Ubuntu and my keyboard is Japanese(by choice) and look |.
Is your keyboard layout set to jp106? If not then run

sudo sudo dpkg-reconfigure

Then make sure to set your keyboard to Japanese. If it IS set to Japanese then make sure your keyboard isn't a weird size and layout. It may be necessary to try another Japanese layout like jp86 etc. If that doesn't work then I'm stumped. It's good to hear from the Japan/Ubuntu crowd!:mrgreen:

---

