---
title: "Is Gourmet Recipe Manager not in the repositories?"
date: 2006-07-21
forum: Desktop Environments
---

### Post by LsrLine on 2006-07-21
The program says it should be in the repositories, but I can't find it.  The website is [http://grecipe-manager.sourceforge.net/](http://grecipe-manager.sourceforge.net/) .  I did a search for gourmet, recipe, etc in synaptic, but it's not coming up.  Any ideas?  Or does anyone know the direct apt-get?  Thanks

---

### Post by orb9220 on 2006-07-22
yep yer right none.

Well I guess it's burger king for you. But on a serious note thier is one called krecipes
ooking book for KDE
Krecipes is a program that lets you to manage your recipes, create shopping
lists, choose a recipe based on available ingredients and plan your menu/diet
in advance.

It uses an embedded SQLite3 database or, if you prefer, MySQL or PostreSQL
to store your favorites recipes.

KDE program but will run on gnome just fine.

---

### Post by LsrLine on 2006-07-28
Can someone point me to how someone would get this program in the repositories... like the process.

---

### Post by CarlesOriol on 2006-07-28
If you want to install it.

You can get DEB file at [http://sourceforge.net/project/showfiles.php?group_id=108118](http://sourceforge.net/project/showfiles.php?group_id=108118) and after install with:

sudo dpkg -i gourmet_0.11.3-1_all.deb

---

### Post by aysiu on 2006-07-28
KRecipes is in the Universe repositories.

Step 1. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

Step 2. Paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install krecipes krecipes-data
```

---

### Post by mrgnash on 2006-11-26
If you're a Gnome user, I wouldn't really bother with Krecipes. It's clunky, buggy, and runs like a dog under Gnome. Gourmet is easy enough to install, even though it **should** be in the repositories, and it's a much more streamlined and easy-to-use program.

---

### Post by justinmiller87 on 2008-04-18
I wrote an install guide for the program. You can get it here: [http://welcometoubuntu.blogspot.com/2008/02/howto-install-gourmet-recipe-software.html](http://welcometoubuntu.blogspot.com/2008/02/howto-install-gourmet-recipe-software.html)

---

### Post by ImpressMe on 2008-04-27
This reminds me... about why Linux will never be able to compete with other desktop OS'es. Why on earth must one consult a forum to understand what happened to a perfectly functioning program after a minor update and why on earth it is still science to install it.

It is a mess.

---

### Post by GavinZac on 2008-06-22
> **ImpressMe said:**
> This reminds me... about why Linux will never be able to compete with other desktop OS'es. Why on earth must one consult a forum to understand what happened to a perfectly functioning program after a minor update and why on earth it is still science to install it.

It is a mess.

Oh yes, because other OS's retain their programs so well when you install the next release! :confused:

Windows breaks programs even with its small updates.
[http://www.google.ie/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=GFB&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=service+pack+breaks&spell=1](http://www.google.ie/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=GFB&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=service+pack+breaks&spell=1)

Back on-topic, GFaim sounds fantastic, except its au Francaise :(

---

