---
title: "Launching matlab in nautilus: simple operations (open m-file, prescribe wd)"
date: 2009-11-03
forum: Education &amp; Science
---

### Post by aimonas on 2009-11-03
hello everyone! I would like to share and at the same time book-keep a few things that have made my life easier while using matlab under ubuntu. 

[COLOR="Red"]1. open m-file with matlab through nautilus[/COLOR]

The concept is to assign a default custom command to open m-files. This is done through right-click-->properties>open with tab-->add-->use a custom command, at which point we input

```
matlab -desktop -r "edit %f"
```

This action however, opens matlab and the editor with the desired file loaded, but leaves the working directory to its default value. I haven't found a way to change the directory simultaneously, so if anyone could give any clue it would be nice.

[COLOR="Red"]2. click on m-file and open matlab at the respective directory[/COLOR]

Same procedure as previously, but we input the following command

```
matlab -desktop -r "cd %d"
```

[COLOR="Red"]3. navigate to any folder in the filesystem and open matlab to work in that specific folder[/COLOR]

a. prepare a small script (let's name it matcd) as follows:

```

#!/bin/sh
matlab -desktop -r "cd %d"

```

b.render it executable through right-click-->properties-->permissions

c. copy it to ~/.gnome2/nautilus-scripts/ and restart system or log out and log back in

then by right clicking inside any folder you can find the script in the submenu scripts. running it will perform the desired action

hope this is useful

cheers

---

### Post by PGScooter on 2009-11-05
thank you! I've pretty much switched to R now, but I still use matlab on occasion for old scripts.

---

### Post by xapuka on 2009-11-26
Hi, 

thanks for the tip! Just one thing, I HAD to use the -desktop flag. Without it doesn't work. By the way, I'm using Matlab 7.50 (R2007b)

Cheers, 

xapuka

---

### Post by monguin61 on 2009-12-16
Thanks for the tips. Does anyone know how to open an m-file with a currently-open matlab session?

---

### Post by perroazul on 2009-12-16
> **monguin61 said:**
> Thanks for the tips. Does anyone know how to open an m-file with a currently-open matlab session?

using matlab's file browser I believe

---

### Post by aimonas on 2009-12-16
through the command window you can use 

edit filename.m

this applies also when you run matlab through the terminal

cheers

---

### Post by monguin61 on 2009-12-16
> **aimonas said:**
> through the command window you can use 

edit filename.m

this applies also when you run matlab through the terminal

cheers



Sorry, I meant to ask if it is possible to open an m-file, through Nautilus (or some other file browser), in the current Matlab session. This works in Windows Explorer and I'm hoping I can get the same functionality in Ubuntu.

Thanks.

---

