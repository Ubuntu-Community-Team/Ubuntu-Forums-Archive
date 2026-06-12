---
title: "how to search for question mark"
date: 2009-06-10
forum: General Help
---

### Post by denarced on 2009-06-10
I have a huge load of files and some them has this symbol which is a question mark in black ellipse .. this is a result of something gone wrong with the text file encoding or something .. 

does anyone know a unix command ( propably a group of em ) with which to search for em ??

---

### Post by CatKiller on 2009-06-10
> **denarced said:**
> this is a result of something gone wrong with the text file encoding or something .. 

It probably isn't. It's probably just that the font you're using in your file manager doesn't have a glyph to display for that character.

---

### Post by blueridgedog on 2009-06-10
What is the result of issuing the command 

```
file /full/path/to/nameofproblemfile
```

Are the characters present when you look at the files in a text editor like vi or nano?

---

