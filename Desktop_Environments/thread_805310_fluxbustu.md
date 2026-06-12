---
title: "fluxbustu"
date: 2008-05-23
forum: Desktop Environments
---

### Post by Th3Professor on 2008-05-23
Okay, well Fluxbox isn't technically a DE... it's just a WM... though I figured this could still go in this category...

Has anybody tried setting up a "fluxbox ubuntu studio"?

---

### Post by sdennie on 2008-05-24
Though fluxbox isn't a DE, you should be able to install it in any Ubuntu flavor.  Just:

```

sudo apt-get install fluxbox

```

It's setup so that at the login prompt, you can click on the Options in the bottom left corner and select to login to fluxbox.  It should also have all the programs that you've installed in the menu you get by right clicking on the desktop.

---

### Post by Abu_Dayya on 2008-05-24
> **vor said:**
> Though fluxbox isn't a DE, you should be able to install it in any Ubuntu flavor.  Just:

```

sudo apt-get install fluxbox

```

It's setup so that at the login prompt, you can click on the Options in the bottom left corner and select to login to fluxbox.  It should also have all the programs that you've installed in the menu you get by right clicking on the desktop.

This will only run fluxbox window manager instead of gnome desktop enviroment. I did it before but with enlightenment not fluxbox.


Now the question is how can we run gnome with fluxbox as its window manager instead of the default gnome and metacity?


Sory Th3Professor for hijacking your thread, but this is realy interesting, and I've been trying to do it for a while.

---

### Post by Th3Professor on 2008-05-24
> **Abu_Dayya said:**
> This will only run fluxbox window manager instead of gnome desktop enviroment. I did it before but with enlightenment not fluxbox.


Now the question is how can we run gnome with fluxbox as its window manager instead of the default gnome and metacity?


Sory Th3Professor for hijacking your thread, but this is realy interesting, and I've been trying to do it for a while.

Oh no you didn't hijack it... it's actually geared towards what I'm shooting for (eventually trying) anyway. :)

Here's one...

Can you still use compiz and the "cube"-effects in fluxbox?

---

### Post by mali2297 on 2008-05-25
> **Th3Professor said:**
> Can you still use compiz and the "cube"-effects in fluxbox?

No, Compiz and Fluxbox are both window managers and cannot coexist.

---

### Post by Abu_Dayya on 2008-05-25
> **mali2297 said:**
> No, Compiz and Fluxbox are both window managers and cannot coexist.

So, when I'm running compiz, GNOME is running compiz as its window manager, not metacity?

---

### Post by atomkarinca on 2008-05-25
> **Abu_Dayya said:**
> So, when I'm running compiz, GNOME is running compiz as its window manager, not metacity?

Precisely. But you can have compositing like xcompmgr. Take a look at [here]("http://fluxbox-wiki.org/index.php/Transparency").

---

### Post by Th3Professor on 2008-05-25
...is there any way, at all, any possible way to get the "cube" (compiz/fusion/etc.) and fluxbox at the same time?

---

### Post by mali2297 on 2008-05-25
> **Th3Professor said:**
> ...is there any way, at all, any possible way to get the "cube" (compiz/fusion/etc.) and fluxbox at the same time?

In Feisty, there was a package called [3ddesktop]("http://packages.ubuntu.com/feisty/3ddesktop"), I haven't tried it myself though.  Here is a [review]("http://linuxreviews.org/features/3ddesktop/").

By the way, why do you want to use Fluxbox?

---

### Post by Th3Professor on 2008-05-26
I'll look into that... looks interesting. :)

---

### Post by angry_johnnie on 2008-05-28
I tried 3ddesktop in fluxbox, and it wouldn't work.  But, oddly enough, it works fine with openbox!  I like 'boxes.' They're very light and very fast, but I also want some eyecandy. :-)

You could combine 3ddesktop, xcompmgr, transset, and some dock, (all in the repos, except for 3ddesktop) and then you'd have a nice, eyecandy'd 'box.'

---

### Post by atomkarinca on 2008-05-28
> **angry_johnnie said:**
> You could combine 3ddesktop, xcompmgr, transset, and **some dock**, (all in the repos, except for 3ddesktop) and then you'd have a nice, eyecandy'd 'box.'

For dock, you can try [wbar]("http://code.google.com/p/wbar/"). It's light and pretty :)

---

