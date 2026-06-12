---
title: "Creating themes with live preview"
date: 2014-06-30
forum: Desktop Environments
---

### Post by startas on 2014-06-30
So, i decided to make my own ubuntu (unity + buntu = ubuntu, to get rid of some obvious future questions) theme or modify existing one, but i'm not really familiar with making themes, and i was wondering if there is any way to make or modify theme and have a real time preview ? Would replacing resourses in current theme and refreshing screen work, or some other way ? Maybe there is special tools for that ? If there aren't, what would be the fastest way to see the changes you made to theme ?

---

### Post by Frogs Hair on 2014-06-30
This may be a possible starting point .  [http://worldofgnome.org/making-gtk3-themes-part-1-basics/](http://worldofgnome.org/making-gtk3-themes-part-1-basics/)

---

### Post by startas on 2014-07-01
The article wasnt helpful actually, it doesnt contain any info about live preview when creating themes, and it was only about the very basics, without a complete tutorial with all information what does what.

---

### Post by vasa1 on 2014-07-01
> **startas said:**
> The article wasnt helpful actually, it doesnt contain any info about live preview when creating themes, and it was only about the very basics, without a complete tutorial with all information what does what.
You'll need to figure out a lot of things for yourself. Unfortunately, documentation isn't exhaustive. 
Re. live preview in the context you specify, AFAIK, that creature doesn't exist.

---

### Post by startas on 2014-07-01
Ok, but if i will edit currently applied theme files, then will it be enough to log off/log on to see the changes ? I will find documentation myself, i just need the fastest way to see the changes, let it be log off/log on, some terminal command or whatever.

---

### Post by vasa1 on 2014-07-01
I don't know about Ubuntu; I use Lubuntu. I think that just by switching to another theme and back to the theme you create is enough for gtk2 applications; you can even have the theme file open at the time . gtk3 applications are, IMO, a bit trickier. You *may* need to log out and log back in.

If you're really keen to mess about, copy the theme over to ~/.themes and play with it in your own folder so you don't need to use sudo (or whatever) all the time. Of course, applications launched with elevated privileges will need extra attention then.

I also don't know anything about qt apps and how they're themed although there are settings to make qt apps follow the current gtk theme.

---

