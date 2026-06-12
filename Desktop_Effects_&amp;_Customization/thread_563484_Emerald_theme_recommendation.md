---
title: "Emerald theme recommendation"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by sunexplodes on 2007-09-30
Right now I'm using XFCE and Compiz Fusion in Gutsy. I have tried a number of things, and can NOT get compiz-fusion to use XFWM as the window manager, so I have to use emerald, which is fine, except I can't find a theme I like. 

I was using Carbonit (xfce/metacity: [http://gnome-look.org/content/show.php/Carbonit?content=45590](http://gnome-look.org/content/show.php/Carbonit?content=45590) ) and I'd love to find something like it. I haven't found anything on gnome-look, and was hoping maybe you guys knew of something, or even better, could suggest something I might like. 

Thanks a bunch!

---

### Post by kakalaky on 2007-09-30
Just use the metacity version of carbonit and gtk-window-decorator instead of emerald

---

### Post by sunexplodes on 2007-09-30
Please be so kind as to humour me:

How?

---

### Post by sunexplodes on 2007-09-30
okay, so i figured out "gtk-window-decorator --replace", but that gives me an ugly theme I've never seen before, and neither the gnome theme editor nor the xfce one allow me to change it. help!

---

### Post by Chymera on 2007-09-30
a screenshot maybe?

---

### Post by sunexplodes on 2007-09-30
> **Chymera said:**
> a screenshot maybe?

I've opened both the Gnome and the XFCE theme managers and no changes can be made, nor does either show THIS as the selected theme. Oh, and neither does Emerald.

---

### Post by sunexplodes on 2007-09-30
I guess I'm in a somewhat overlooked minority, running CF on XFCE. Does anybody know of a way to use the XFCE window manager with Compiz? Or am I stuck here?

---

### Post by Ant1jr on 2007-09-30
If you can run compiz-fusion dont use xfce

---

### Post by Caligula on 2007-09-30
> **Ant1jr said:**
> If you can run compiz-fusion dont use xfce


why exactly?
people aren't only using xfce on slow computers, a lot of people like the environment. It's a great DE.

---

### Post by sunexplodes on 2007-09-30
Yeah, that's ridiculous. I like the XFCE environment. Thunar is a better file manager than Nautilus, IMO. XFCE handles a desktop better. It's snappier. XFWM4 is in general, a more fully-featured WM than Metacity.  It has better display controls than gnome. I could go on, but I'd rather just stick to why I made the thread.

Any ideas on using XFWM with Compiz? Or alternately, any good themes similar to Carbonit that anyone would suggest?

---

### Post by kakalaky on 2007-10-01
you need enough of gnome installed to have /apps/metacity/general/theme in gconf and you can set the theme there.

Edit:  Found a better way:

```
gtk-window-decorator --replace --metacity-theme THEME
```

---

### Post by sunexplodes on 2007-10-01
> **kakalaky said:**
> you need enough of gnome installed to have /apps/metacity/general/theme in gconf and you can set the theme there.

Edit:  Found a better way:

```
gtk-window-decorator --replace --metacity-theme THEME
```

Ohman, that is promising, but nothing changed. 

I ran "gtk-window-decorator --replace --metacity-theme Carbonit" and it popped up with the same ugly theme as before. I have gnome installed, I just prefer not to use it. I've got everything the default ubuntu installs, plus xubuntu-desktop.

[ATTACH]45045[/ATTACH]

---

### Post by kakalaky on 2007-10-01
You probably need to give it the full path to the theme.

Edit:  If that doesn't work try extracting the attached file in ~/.gconf/apps/metacity/general/

---

### Post by sunexplodes on 2007-10-01
Hrm. Still nothing, with either of those options.

Oh well. I managed to find an emerald theme I like, and modified it to a point where it's pretty close. 

Thanks anyway.

---

### Post by Chymera on 2007-10-06
hmmm.... if you ask me that theme is rather sexeeh :P.... in a more on-topic fashion however, have you tried ```
emerald --replace &&
``` ?

---

### Post by tonic on 2007-10-07
Read here about how to use gtk-window-manager

you might find gconf-editor useful

[http://wiki.compiz-fusion.org/Decorators/GTKWindowDecorator](http://wiki.compiz-fusion.org/Decorators/GTKWindowDecorator)

---

