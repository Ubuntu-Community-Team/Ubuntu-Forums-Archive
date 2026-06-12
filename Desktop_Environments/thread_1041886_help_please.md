---
title: "help please???"
date: 2009-01-17
forum: Desktop Environments
---

### Post by kylem1989 on 2009-01-17
ok so im trying to install a theme for my Ubuntu desktop and when i try to install it the error is saying that my file format is wrong... what can be the problem?

---

### Post by kylem1989 on 2009-01-17
BTW im running on Ubuntu 4.07 Fiesty Fawn..

---

### Post by 3rdalbum on 2009-01-17
> **kylem1989 said:**
> BTW im running on Ubuntu 4.07 Fiesty Fawn..

That's an interesting version... you mean Ubuntu 7.04, I assume.

Your theme is in a .tar.gz file, right? Tell the Appearance (or Themes) program to install the .tar.gz. Don't uncompress it first.

If it's any other sort of theme (.emerald, Qt or something different) then it's not compatible with the Themes program.

---

### Post by kylem1989 on 2009-01-17
> **3rdalbum said:**
> Your theme is in a .tar.gz file, right? Tell the Appearance (or Themes) program to install the .tar.gz. Don't uncompress it first.


here is what i do and i get that error....

System-> prefrenses->theme-> install theme 

then when i click the theme to install i get the error " The file format is invalid"

What should i do?!?!?!?


and yes 7.04

---

### Post by taurus on 2009-01-17
What is the name of the file and where did you download it?

---

### Post by kylem1989 on 2009-01-18
its every file i try to put on, anything i try to install doesnt work (theme wise)

---

### Post by melojo on 2009-01-18
> **kylem1989 said:**
> here is what i do and i get that error....

System-> prefrenses->theme-> install theme 

then when i click the theme to install i get the error " The file format is invalid"

What should i do?!?!?!?


and yes 7.04


It states exactly what is wrong.
Give us the name of the file and where you got it just like taurus suggested!!

---

### Post by kylem1989 on 2009-01-18
gnome-look.org


/home/kyle/Desktop/gtk2-engines-nimbus-0.1.1-felicia-all.tar.gz

---

### Post by kylem1989 on 2009-01-19
can someone tell me whats wrong?

---

### Post by mcduck on 2009-01-20
> **kylem1989 said:**
> gnome-look.org


/home/kyle/Desktop/gtk2-engines-nimbus-0.1.1-felicia-all.tar.gz

Based on the name, that is not a theme, it's a GTK engine (practically a program themes use to draw different kinds of widgets).

If you still wish to install it, extract the package somewhere and read instructions inside. (Most likely the package contains source code for the program, ad you'll need to compile it.)

Edit: there are also .deb packages of that GTK engine available at Gnome-look.org. You'd better use them instead of compiling the engine from source: [http://gnome-look.org/content/show.php/?content=97717]("http://gnome-look.org/content/show.php/?content=97717")

---

### Post by ajcham on 2009-01-20
> **mcduck said:**
> Edit: there are also .deb packages of that GTK engine available at Gnome-look.org. You'd better use them instead of compiling the engine from source: [http://gnome-look.org/content/show.php/?content=97717]("http://gnome-look.org/content/show.php/?content=97717")

Actually that link is for exactly the same file the OP has already downloaded.

kylem, just extract the archive you already have - it will contain two deb files: **nimbus-icon-theme…** and **gtk2-engines-nimbus…**.  Install the icon theme first (just double click the deb), then the GTK engine.  You'll get a dependency error if you try installing the engine first.

---

