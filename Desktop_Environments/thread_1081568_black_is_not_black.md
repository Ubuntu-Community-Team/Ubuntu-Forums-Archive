---
title: "black is not black"
date: 2009-02-26
forum: Desktop Environments
---

### Post by destiney on 2009-02-26
Ubuntu [broke my konsole the other day]("http://ubuntuforums.org/showthread.php?t=1071691") so now I'm trying to get by using gnome-terminal.

My problem is that when I run Emacs in gnome-terminal the background is no longer black, it's a cloudy, dark gray color.

Anyone know why black would be rendered correctly in konsole but not in gnome-terminal?

[http://static.destiney.com/konsole_broken_but_emacs_black_is_black.png]("http://static.destiney.com/konsole_broken_but_emacs_black_is_black.png")

[http://static.destiney.com/gnome_terminal_works_but_black_is_grey.png]("http://static.destiney.com/gnome_terminal_works_but_black_is_grey.png")

---

### Post by smani on 2009-02-26
Have a look in edit->profile preferences->colors

---

### Post by destiney on 2009-02-26
> **smani said:**
> Have a look in edit->profile preferences->colors

It's set to black.

I guess I should clarify.. my gnome-terminal is actually black before starting Emacs.  The background color in Emacs is not black like it is in konsole.

---

### Post by FrankT-Qc on 2009-05-05
Same for me.

You might have noticed that this seems to be a ncurses thing (aptitude will have the same "dim black" problem...)

Unfortunately, I have not found a solution yet...

---

### Post by FrankT-Qc on 2009-05-17
I got it !!

Ahahah it was so easy... and I've been googling for hours on this !

If you go into the menu then Edit->Profile Preferences you have a tab called "Colours". In this tab, you can modify the color palette... The first color is "black" and somehow, with the "Tango" scheme, "Black" is set to some grayish yuckish color... Just switch theme to "Linux console" or change just the first color to black (or fuchsia... )

Have fun, 
Frank

---

