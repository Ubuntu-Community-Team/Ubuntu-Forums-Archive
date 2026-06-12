---
title: "HOWTO Easily change the colors of your conky"
date: 2009-01-03
forum: General Help
---

### Post by evilkastel on 2009-01-03
This is aimed to beginners mainly, because most advanced users are very likely to know this tip already.
If you are like me,you change your GTK,Window decoration and wallpaper on regular basis. The Issue comes when I realize, my .conkyrc is set to color that do not match my current theme.

So, just do 
```
vim ~/.conkyrc
```

That will open Vi Improved, text editor. navigate the file with the arrows, and Identify The colors. Example: Tan1, Tan2, DimGrey, DarkGray...
With The color you want to change identified, (compare the colors you found with the colors you see in your conky...duh) type while still in vim:
```
:%s/ActualColor/NewColor/g
```
Replacing with your colors.
Then do:
```
:wq
```
to exit vim and return to bash, while saving, and restart conky.
```
pkill conky
```
```
conky
```
And thats it.

NOTE: I couldn't find a comprehensive list of all colors possible in conky, but i find that most color names, and that names with the prefixes "Dim" or "Dark" will work.

---

