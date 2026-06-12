---
title: "Changing the Seperator's image??"
date: 2009-04-20
forum: General Help
---

### Post by AbsentHarvest on 2009-04-20
[http://i544.photobucket.com/albums/hh324/NOD62/Screenshot-3.png](http://i544.photobucket.com/albums/hh324/NOD62/Screenshot-3.png)

Look at the top left side of the screen, can you see the 12 white dots (6 in 2 rows) this is a seperator.  I'm wondering if I can change the image of it as I believe this is part of the icon theme I installed.  I would like to change this into something that blends better with my background or even possibly removing this seperator so that only the notifier shows up.  Am I able to achieve this?

---

### Post by sdennie on 2009-04-20
Of course.  Try the following three commands to figure out where the image is located:

```

find /usr/share/icons -name "*separator*"
find ~/.icons -name "*separator*"
find ~/.themes -name "*separator*"

```

Then just replace the offending file with something you prefer.  You will likely have to logout or do some theme juggling (changing to another and then back) to notice the changes.

---

### Post by AbsentHarvest on 2009-04-20
well, i can't find it with those search entries... however you had me going on the right track, i also looked around prodding and found that the picture i'm trying to change is located in the Appearence > Customize > Control > Glossy.  A default theme

just trying to find it..

---

### Post by AbsentHarvest on 2009-04-20
tried /usr/share/themes/Glossy but there is no icons in there. :S

---

### Post by sdennie on 2009-04-20
My advice is probably wrong.  But, it's a good push in the right direction.  Those are the places where icons and themes are stored.  If you look around enough, you'll find what you are looking to change.  Another place to look is /usr/share/themes.  In fact, that's a likely spot to look.

---

### Post by AbsentHarvest on 2009-04-20
Yeah that's where I looked before.  I found the theme I am using... Glossy but when I go into that folder, there are no images to be found... that's what has me perplexed at the moment.

---

### Post by sdennie on 2009-04-20
Most themes are only partially implemented and fall back on more well established themes.  The imagine you posted makes me think your theme is falling back on Tango or something similar for things.

Edit:
Could also be Human or Tangerine

---

### Post by AbsentHarvest on 2009-04-20
All the themes (default themes) in /usr/share/themes are pretty much empty.  A few have a couple of images in a metacity folder but the rest only have xml spreadsheets and in the gtk2.0 folder all there is a text document called gtkrc in all of them.

---

### Post by AbsentHarvest on 2009-04-20
I was reading the document in the Glossy theme, and apparently the engine it's using is Clearlooks.  Human theme also has this seperator and like it's gtkrc it also states that it's using the Clearlooks engine.. I don't know if this has anything to do with it.

Human, Human Glossy, Clearlooks, Clearlooks Classic and Glossy have the same seperator.  There is no images in the /usr/share/themes/*name of theme*..... just the gtkrc file and a index.theme

---

### Post by AbsentHarvest on 2009-04-20
Solution: Removing the handles all-together.
How?

[http://ubuntuforums.org/showthread.php?t=637349&page=2](http://ubuntuforums.org/showthread.php?t=637349&page=2)
;)

---

