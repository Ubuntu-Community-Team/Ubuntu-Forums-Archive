---
title: "Needs some help with rename"
date: 2009-01-23
forum: General Help
---

### Post by Swords on 2009-01-23
I'm trying to rename a batch of files that are giving me sorting issues. The files have names like "PA1_Chapter_One1.jpg" to "PA1_Chapter_One14.jpg". This causes tons of sorting errors because 10 follows 1 and 20 follows 2, so I want to replace 1-9 with 01-09. Easier said than done.

I've tried a bunch of things like 
```
rename s/[^0-9][0-9]\.jpg$/$1\0$2.jpg/ *.jpg
```
and what I get is that it tries to rename them all to "PA1_Chapter_On0.jpg", apparently just throwing away the two matched characters. I assume it's a problem with my expression, so hopefully someone more experienced with perl can correct me.

---

### Post by sdennie on 2009-01-23
Maybe try:

```

rename s/([^0-9])([0-9])\.jpg$/$1\0$2.jpg/ *.jpg

```

---

### Post by Swords on 2009-01-23
I have tried that, but it gives me a syntax error: unexpected token `('. I thought it didn't make any sense, but bash probably knows better than I.

Edit: Enclosing the string you suggested in quotes gets rid of the error, but now saying "PA1_Chapter_One2.jpg not renamed: PA1_Chapter_On.jpg already exists", yet instead of a "PA1_Chapter_On.jpg" in the directory, it's now just "PA1_Chapter_O".

---

### Post by sdennie on 2009-01-23
Try single quoting the regex:

```

rename 's/([^0-9])([0-9])\.jpg$/$1\0$2.jpg/' *.jpg

```

---

### Post by Swords on 2009-01-23
That's quite a bit closer. At least now it's renaming the files to their original names. I'm pretty sure the reason it isn't adding the 0 now is that the \0 I used isn't the proper way to separate it from the $1.

Edit: Found it! Just needed to add {}'s around the 1. I thought that was how it was done but it was giving me errors earlier. I guess they were unrelated.

Here's the command for anyone interested:

rename 's/([^0-9])([0-9])\.jpg$/${1}0$2.jpg/' *.jpg

---

