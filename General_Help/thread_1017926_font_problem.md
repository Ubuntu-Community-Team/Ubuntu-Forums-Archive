---
title: "font problem"
date: 2008-12-21
forum: General Help
---

### Post by ahounsome on 2008-12-21
Hi Guys, can anyone help with an issue I've got with Flash. There's one file i need to edit and everytime I open it up i get a font missing message. I have the fonts and have tried installing them via Konqueror, and I've created a .fonts directory and put the 3 fonts in there, but to no avail. I'm running Hardy.

---

### Post by empthollow on 2008-12-21
try this.  It will update the font information
```
fc-cache
```

---

### Post by ahounsome on 2008-12-21
no good I'm afraid - same problem

---

### Post by lostandcold on 2009-01-21
This worked for me.

```
gksudo nautilus
```

Then copy and past the fonts into the directory /usr/share/fonts/truetype
(i'm assuming it's a truetype font)

and then run the following command

```
sudo fc-cache -fv
```

and everything will hopefully work.

And if not there are a lot of other ways to essentially do the same thing that are also worth trying just search through the forums some more to find them.

---

### Post by lostandcold on 2009-01-21
Actually since you sre using konqueror I assume you are using KDE and therefore the code 

```
gksudo nautilus
```

Probably won't be of great help to you.

Sadly I am too ignorant to know the equivalent for KDE.

---

