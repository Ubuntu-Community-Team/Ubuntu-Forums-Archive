---
title: "Gnome fat typing  cursor"
date: 2007-10-12
forum: Desktop Environments
---

### Post by Tritis on 2007-10-12
I would like to have the typing default cursor be the fat one instead of the thin one.


You can see the fat cursor by entering overwrite mode (by hitting insert in a text box of an application that isn't firefox.)

I checked the gconf-editor but the only options I could find were to change the blink rate.

---

### Post by eurgain on 2007-10-12
I do not think this can be done... (I may be wrong).  Here is why.

The point of the cursor is to show you where your keyboard input will appear.

In normal (insert) mode, your input is logically between two characters or at the end of a line.  Therefore, the cursor, which is a physical (albeit graphical) thing, tries to represent this as being a logically infinitely thin (but physically, just very thin)  line that is between two character positions.

In overtype mode, your input is logically *on* a character.  Therefore, the cursor is a physical representation of that -- it is upon the whole character your next keyboard input will replace.

Some very old (and I mean **very** old - like 1970s) terminals used a block cursor in insert mode, and shuffled the whole line of characters around the cursor if you moved it along the line using the arrow keys.*

Therefore, simply replacing a line (or I-bar) cursor with a block cursor, would break the logical model that a modern GUI aims to present to the user.

HTH
A

*Just shows how long I have been using computers. Gulp!  I remember using this on old green-screen 40*80 monitors, and being delighted by "screen editing", which was sort of like a very basic version of vi.  I never did paper teletypes, but I think that it is thirty years ago this year that I first moved a glowing green blob along a line of Pascal code!

---

### Post by Tritis on 2007-10-13
gnome-terminal seems to do a fine job of using the fat cursor in insert mode.

[[IMG]http://img90.imageshack.us/img90/16/fatcursorfh1.th.png[/IMG]]("http://img90.imageshack.us/my.php?image=fatcursorfh1.png")

---

