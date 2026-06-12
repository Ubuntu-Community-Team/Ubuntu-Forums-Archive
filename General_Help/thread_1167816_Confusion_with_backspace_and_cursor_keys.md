---
title: "Confusion with backspace and cursor keys"
date: 2009-05-23
forum: General Help
---

### Post by rost78 on 2009-05-23
Hello,
 
 

I've just installed Ubuntu 9.04 with Gnome and I'm already encountering my first problem. When editing a text file with vi I'm getting confused with the backspace key and the cursor keys.
[LIST]
[*]The backspace key only moves the cursor to the left without deleting the character.
[*]When changing to insert mode, the cursor keys do not move the cursor. Instead, they insert the characters A (up), B (down), C (right) and D (left).
[/LIST]Does anybody know this issue and is able to help?
 
Thanks :)
 
Robert

---

### Post by Kareeser on 2009-05-23
Yep. Vim's not terribly user friendly, since it's got a moderate learning curve.

Try using "nano" to do your editing, you'll find it's much more intuitive.

Vim's quite powerful if you want to get into it, but for the casual tweaker, nano is more than powerful enough!

---

### Post by asmoore82 on 2009-05-23
Ubuntu ships with the "vim-tiny" package, anyone who even knows of
vim's existence will probably want to replace this with a full featured package:
```
sudo apt-get install vim-full
```
-AND/OR-
```
sudo apt-get install vim-gnome
```

---

### Post by rost78 on 2009-05-25
@asmoore82
Perfect! Thanks so much :D
 
@Kareeser
I'm pretty much used to vim so I know the basic handling. asmoore82's hint is what I've been looking for.

---

