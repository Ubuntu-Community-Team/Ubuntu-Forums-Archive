---
title: "Close button color"
date: 2010-12-01
forum: Desktop Environments
---

### Post by specialblend on 2010-12-01
Hi I hope this is an easy question,

I just want to change the color of the close button on windows of the Ambiance theme from the orange to blue.  I copied the theme from usr/share into my .themes folder so I don't mess with the original, and then I just changed the name to Blue Ambiance and changed the appropriate .png files I found in the metacity folder to blue. When I select this new them in my appearance menu though nothing changes.

Am I doing this all wrong?

---

### Post by Frogs Hair on 2010-12-01
Take a look at this. [http://gnome-look.org/content/show.php/Ambiance+blue?content=133676](http://gnome-look.org/content/show.php/Ambiance+blue?content=133676)

---

### Post by bvc on 2010-12-01
Should be able to change the name to Blue Ambiance in the index.theme and metacity-theme-1.xml files. However when I tried it, the modified close.png is replaced with the original close.png :shock: . This happens repeatedly....
Replace with mine
refresh (F5) in nautilus
and it's replaced with original

---

### Post by bvc on 2010-12-01
Copying the buttons from Ambiance blue on gnome-look.org worked. So you probably just need to edit the above mentioned files.

---

