---
title: "Gnome Themes Messed Up?"
date: 2006-12-04
forum: Desktop Environments
---

### Post by TrendyDark on 2006-12-04
I'm having a problem with my GTK themes, every time I switch from Clearlooks or what-not, the seperators on the gnome panels look messed up and ugly, I can't seem to find a theme that doesn't look like this.

Also, I have replaced every distributor-logo.png file I could find on my disk, but I still see an Ubuntu logo :-/](*,)

---

### Post by engineer on 2006-12-04
try reinstalling gtk-themes and gnome-panel. maybe some library path or version is wrong.

i changed the distributor logo. but i can't remember where it was. it took some time for me too. did you look for it in ~/.icons?
i think i changed it there

---

### Post by TrendyDark on 2006-12-04
I actually changed it in every theme, but you're only supposed to change it for "hicolor". Run "locate distributor-logo.png" in the terminal, you'll see what I mean.

Is it safe to reinstall gtk and gnome-panel?

---

### Post by engineer on 2006-12-04
well what could go wrong?

you could also try to kill gnome-panel and start it from command line.
maybe you get some errors about missing libraries or theme files.

---

### Post by TrendyDark on 2006-12-04
When I kill Gnome-panel, it reloads itself automatically, anyway to stop that?

---

### Post by Perfect Storm on 2006-12-04
Try re/installing gtk2-engines-pixbuf and see if it helps.

---

### Post by engineer on 2006-12-04
you'll have to remove it from session first.
you can do that in the control cente. (System->Preferences->Session)

and reinstalling gtk-engines-pixbuf is a good idea. i thought gtk-themes would contain all these engines. that's why i just wrote about gtk-themes

---

### Post by TrendyDark on 2006-12-04
AI, would it have been the source of the problem if gtk2-engines-pixbuf was not installed? (I just installed it)

---

### Post by Perfect Storm on 2006-12-04
It might, I only had the problem on 6.10 not 6.06

---

### Post by TrendyDark on 2006-12-04
Oh crap, I need to change that. 

I just built a new computer Friday and I installed 6.10 (old comp had a problem with the kernel and a package).


***EDIT*** Thanks for your help guys! AI, your solution worked for me! Thanks a million!

---

