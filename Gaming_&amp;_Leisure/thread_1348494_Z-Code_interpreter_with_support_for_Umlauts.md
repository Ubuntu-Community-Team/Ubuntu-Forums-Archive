---
title: "Z-Code interpreter with support for Umlauts?"
date: 2009-12-07
forum: Gaming &amp; Leisure
---

### Post by Klaue on 2009-12-07
I search an interpreter for Z-Code which supports german umlauts (äÄöÖüÜ).
FYI: Z-Code is compiled code ("story files") from the inform language, which is used for nearly every Textadventure out there.

Now, I found 3 Z-Code-Interpreters for Linux:
- Frotz, a port of the Windows version using ncurses
  Problem: Displays Umlauts as ?-Symbols
- Xzip, a GUI version
  Problem: Displays umlauts correctly, but you can't enter them (Error message "Key <ä> not bound")
- Jzip, a Text-Only-Version of XZip, as far as I can see it also uses ncurses
  Problem: Same as for Frotz

Does anyone know an interpreter for the story files that can handle umlauts?

Maybe the display problem of frotz and jzip is a problem of ncurses and if yes, how could I fix that?

Note: My terminal itself has no Problems at all with umlauts

---

### Post by BoyOfDestiny on 2009-12-07
Looking at 
man frotz

frotz -p somegame

Sadly, this doesn't support the umlauts, but puts the right letters, rather than a "?"

There are many ports listed on the frotz page, including other interpreters, some which are platform independent:
[http://frotz.sourceforge.net/](http://frotz.sourceforge.net/)

I will update this post if I find a better solution for frotz...

---

### Post by Klaue on 2009-12-07
Thank you, BoyOfDestiny
I saw this param in the man file, but I never thought about using it (I was searching for a "use UTF8" option at the time, but that seems to be the default anyway)
It would be an usable workaround, but I just found an interpreter that works, Gargoyle
[http://ccxvii.net/gargoyle/](http://ccxvii.net/gargoyle/)
It's a nice one which can understand way more than just z-code and works flawlessly with umlauts. Also, I always loved gargoyles.
Nothing for a headless system, but perfectly fit for my purposes. the only thing I miss is the lack of full screen, but that's not really important

Soo, I'm happy with that solution, no need to further investigate frotz :)

---

