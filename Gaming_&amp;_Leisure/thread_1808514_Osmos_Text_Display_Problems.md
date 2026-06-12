---
title: "Osmos Text Display Problems"
date: 2011-07-20
forum: Gaming &amp; Leisure
---

### Post by dragonboss on 2011-07-20
Installed osmos and there is no text displayed in any menus. How do I fix this?

---

### Post by conradin on 2011-07-20
hmm... Ive nver seen that issue, but it is graphics intensive.
can you launch osmos from the terminal and observe any stderr that might occur? Just a thought. maybe youre missing a font?
have you tried pressing any keys to see if it will load further than the menu?
I think "n" starts a new game, "x" quits.

---

### Post by dragonboss on 2011-07-20
It does load further,and since I have installed it before on my laptop, the buttons i know work. Example esc and then x to quit.

---

### Post by thatguruguy on 2011-07-20
It's a problem with the "Fortune City" font, which you will find in /opt/Osmos/Fonts.  Replace the font with a different one, and it will solve the problem. 

Here's the easy way to do it, substituting the Ubuntu font for the Fortune City font:
```

sudo cp /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf /opt/Osmos/Fonts/FortuneCity.ttf

```

---

### Post by dragonboss on 2011-07-20
Worked like a charm. Thank you!

---

### Post by Paul5mith on 2012-01-08
The described problem occurs in Osmos version 1.6.0. An update is available which fixes the issue in Osmos version 1.6.1. Tested on Ubuntu 11.04.

---

