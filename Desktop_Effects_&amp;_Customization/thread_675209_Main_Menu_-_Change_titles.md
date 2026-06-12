---
title: "Main Menu - Change titles?"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by Blice on 2008-01-22
Hi.

I would like to change the parts where it says "Applications" "Places" and "System" to something else.

How can I do that?

Thanks.

---

### Post by user1397 on 2008-01-22
> **Blice said:**
> Hi.

I would like to change the parts where it says "Applications" "Places" and "System" to something else.

How can I do that?

Thanks.hmm, I am not exactly sure thats so easy to do; try right clicking on them > edit menus and see if you can do it there, if not, enable the gnome configurationeditor in the same menus editor, itll be under applications > system tools > configuration editor

im not on my ubuntu pc right now so i cant directly tell you

---

### Post by Blice on 2008-01-23
So... I thought maybe I'd use the translation files for it; the .po files in the source that're compiled into the .mo files.

I found "Applications" in all of them, yet they lack "Places" and "System", which doesn't make sense to me. 

I searched the entire source folder for text containing "Places", and only found 5 or 6, where every time it was just something like "replace". 

I don't know what to do. Right now I'm doing a regex search on all files in my system for ("|'| )(Applications|Places|System)("|'| ) 

I hope someone can help me with this, I'm not sure what else to do at this point.

Edit: Okay, the source I had was an older version. I downloaded 2.20.2, and in its .po files it has the Places/Applications/System defined.

Now to change and compile...


Edit2: One discomfort I have before I compile here... The line numbers for panel-menu-items.c are different in the different languaged .po files. Example:

From the en_CA po:
#: ../gnome-panel/panel-menu-items.c:953
msgid "Places"
msgstr "Places"


Then, from the en_GB po:
#: .../gnome-panel/panel-menu-items.c:910
msgid "Places"
msgstr "Places



Why is one 953 and the other 910? Makes no sense...

Edit3: Okay, so, I made the new .mo file for en_CA, and replaced the gnome-main-menu.mo in the en_CA folder with it. I logged in and switched my language to English (Canada), and it didn't work. The text stays the same. -sigh-

Edit4: I tried to replace the en_CA one with some other language with some weird characters etc.; I logged out, re-selected my language back to en_CA, logged back in, and it's still the same. So obviously gnome-main-menu.mo doesn't actually translate the main menu. What the hell is this file for?

---

### Post by Blice on 2008-01-23
Bumping this; I still need to figure it out. I don;t know how to make the gnome-main-menu.mo to work.

---

### Post by user1397 on 2008-01-27
worth a try: ```
killall gnome-panel
```restarts  the gnome panel and refreshes any changes

---

