---
title: "Keyboard problem - pretty sure keyboard is OK!!!"
date: 2009-03-28
forum: General Help
---

### Post by iamhigh on 2009-03-28
Folks - I finished installing Ubuntu on my machine. dual boot with XP.

On Ubuntu I have a peculiar problem with the Double Quotes/Single Quote ¨ ´ Key.

First noticed the problem when working on Eclipse where it says the quotes are invalid tokens. 

The quotes type OK - e.g: ¨ ¨ ¨ ¨ ¨ - but for whatever reason are not recognized correctly?

xev reports a "&#65533;" on this key press. 

Any clues what can I do to correct this? tried a couple of layouts etc to no use.

Works perfect on Windows XP!

Please advise.

---

### Post by dandnsmith on 2009-03-28
First have a look at the XP settings, since these work.

Control Panel|Keyboards
Control Panel|Regional and Language Options (all the tabs ...)

You can then look at the Ubuntu settings to see if you can spot the deficiency, and possibly in the xorg.conf you have for the types used there.

---

