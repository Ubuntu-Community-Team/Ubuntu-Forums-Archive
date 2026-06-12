---
title: "HOWTO: Make the new Deskbar not look quite so terrible"
date: 2008-03-10
forum: Desktop Effects &amp; Customization
---

### Post by ElTimo on 2008-03-10
Before you begin: This will ONLY work under Compiz/Beryl, as I have yet to figure out how to do this under Metacity.

First, open up Advanced Desktop Effects Settings by going to System -> Preferences -> Advanced Desktop Effects Settings or by pressing alt+f2 and typing ```
ccsm
```

Then, go to the section under Effects labeled "Window Decorations" and change the entry under "Decoration Windows" from ```
any
``` to ```
 any&!(name=deskbar-applet)
```and press enter. That's all! you can reposition the search box by using alt+click and dragging it to wherever you want it. Hope this helps someone.

---

### Post by hyperair on 2008-03-10
In Ubuntu Hardy, it's possible to set Deskbar to glue onto the panel like it used to back then. It's in the last tab in Deskbar Preferences. "Stick to panel". I'm not sure whether Gutsy has it.

---

### Post by ElTimo on 2008-03-10
Gutsy does not have this option (trust me, I've looked ;)). I did see, however, that the creator of Deskbar was getting a LOT of crap from the community because of the way the interface was set up, and i also saw that he was planning on fixing it, but I was unaware that he actually HAD fixed it :P In this case, consider this post a howto for people who don't want to/don't know how to upgrade the applet. Thanks for pointing this out to me though. I'll have to give it a look. What version does Hardy use?

---

### Post by ElTimo on 2008-03-10
Ok, I installed the most up-to-date version of deskbar-applet i could find (as of now, 2.21.92) and you are, in fact, correct. Thanks for pointing this out to me! :-D

---

### Post by hyperair on 2008-03-10
Awesome. I was rather annoyed with the change in Deskbar's look, but when this look came back I immediately switched. Well, as fast as I found out anyway. I just happened to be poking around the configuration.

---

