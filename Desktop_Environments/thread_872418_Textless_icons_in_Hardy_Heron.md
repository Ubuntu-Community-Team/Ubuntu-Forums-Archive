---
title: "Textless icons in Hardy Heron"
date: 2008-07-28
forum: Desktop Environments
---

### Post by wickstopher on 2008-07-28
Is it possible to have icons on the desktop without any text in Hardy Heron?  The trick of leaving the name blank or as a space in icon preferences no longer seems to be working.  I'm tearing my hair out, because I feel like this should be easy (and from what I recall, was easy in older versions).  What am I doing wrong?

---

### Post by wickstopher on 2008-07-29
bump? :)

---

### Post by Zimmer on 2008-07-29
Menu and toolbar preferences.
should be an option for text alongside , text only, icon only

Dapper, yes, but there should be a tab for icons in the Customize theme GUI in Hardy?

under Appearance, I would think

---

### Post by wickstopher on 2008-07-29
Definitely not finding it anywhere.

---

### Post by Zimmer on 2008-07-29
try configuration editor...
desktop>gnome>interface>toolbar_style   and change the value to icons

---

### Post by wickstopher on 2008-07-29
Hmm...I already have "toolbar_style" set to "icons."  Still get text beneath the icons on my desktop.

---

### Post by Zimmer on 2008-07-29
Just tested in Dapper, removed text from icons on application toolbars.
Just exactly which text and icons are you talking about on the Desktop??

---

### Post by wickstopher on 2008-07-29
The icons (i.e. application launchers, etc.) that reside on the actual desktop.  I'm setting up a system for my daugther, and I want oversized icons without text on the desktop that sort of fit in with her wallpaper.  I had this before in Gutsy, and for some reason it won't allow me to do it in Hardy.  Before, all you had to do was right-click on the icon, and change the name of the icon to a space, and there would be no text shown for the icon on the desktop.  It no longer allows you to do that (it reverts back to the icon/launcher's original name).

---

### Post by Zimmer on 2008-07-29
worse, in Dapper a blank will set it to bring in the developer name, details running to  a few sentences of text!   a small full stop (a single character, obviously, makes it 'almost' blank...   hmmm....

---

### Post by Kundera on 2008-07-29
I just hit this thread while searching for a solution myself.
I suspected, that maybe "invisible" characters other than space might work.
I just tried something out of the character table, although I can't tell you which character I chose, and inserted this one when renaming the icons.

Good Luck :)

Kundera

EDIT: One that is working is called "U+FE0D VARIATION SELECTOR-14"

---

### Post by wickstopher on 2008-07-30
Here's a screenshot of what I'm trying to do.  This was my daughter's desktop before I installed Hardy Heron on her computer (before, I was using Linux Mint Daryna, which is based off of Gutsy IIRC).  All of the large icons on the desktop are either launchers for applications or for websites via Firefox.  I'm not sure if I follow the previous poster as per the "invisible characters," and I'm not sure if that is exactly what I'm going for.  Thanks again for any help.

[IMG]http://farm4.static.flickr.com/3055/2677273392_423661c978.jpg?v=0[/IMG]

---

### Post by Kundera on 2008-07-30
Hi wickstopher,

On Gutsy there was the option of just renaming an icon with a single "space", then the icon text was gone. This does not work any longer on Hardy. But if you use the character map (that seems to be the way it is called in English)  and select another character that is as "invisible" as space, then it should work. You can find the character map at Applications > Accessories > Character Map. There is a search function included, if you just search for U+FE0D you should find one of the characters I mean. Just copy it and insert it via ctrl+V when renaming your icons.
That worked fine for me :)
Screenshot: (the "TEXT" and "FFOX" things are the icons ;) )

[[IMG]http://c.imagehost.org/t/0695/Bildschirmfoto.jpg[/IMG]](http://c.imagehost.org/view/0695/Bildschirmfoto.png)

---

