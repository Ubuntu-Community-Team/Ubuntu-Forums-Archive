---
title: "lightweight compositing?"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by crazybilly on 2007-09-17
I've got an Acer Aspire laptop with an integrated/shared SiS video card.  Compiz is right out.

But I'd like to be able to do some transparency stuff and have some decent dropshadows without dinging my performance too much.  From a performance standpoint, xcompmgr works pretty well. 

However, I still get the problem where if I hit my power button to logout, I can't see the dialog. The trade off's not really worth it for me, so I unless there's another option, I think I'm going to pass.

Is there a good way to work around that (other than learning the pnemonics for each option or logging out to gdm)?  Or is there something else out there like xcompmgr that I should try?  Thanks!

---

### Post by aidanr on 2007-09-17
try xfce?

---

### Post by ahaslam on 2007-09-17
You could try xfce, it uses xcompmgr but has a nice GUI for the settings & integrates itself well. Just install xfce4, not the entire 'desktop' meta package.

---

### Post by loell on 2007-09-17
how about spiftacity? it is supposed to be an alternative metacity with compositing enabled

---

### Post by hyperair on 2007-09-17
Are you sure that even works? I tried it and it segfaulted when I tried to run it.

---

### Post by loell on 2007-09-17
me? nope , that's why I left a question mark there. 
i guess its useless fiesty package, i hope it will work in gutsy

---

### Post by hyperair on 2007-09-17
There's always KDE =P

---

### Post by loell on 2007-09-17
actually its kwin :p 

at KDE 4 though

---

### Post by hyperair on 2007-09-17
Heh I just tried running KDE4 from feisty-backports.. it seems that it's screwed for the moment =\

---

### Post by Forlong on 2007-09-17
> **crazybilly said:**
> However, I still get the problem where if I hit my power button to logout, I can't see the dialog.
You can use the standard GNOME-dialog instead (but then you will be only able to log out and switch the user - no hibernate etc):
First run
```
gconf-editor
```
then enable the following key: **/apps/panel/global/upstream_session**
And restart your panel:
```
pkill gnome-panel
```

---

### Post by raul_ on 2007-09-17
e17 also has a module for compositing...but the regular eye candy is much superior :)

---

### Post by crazybilly on 2007-09-17
I tried knome last night (using kwin instead of metacity).  It wasn't bad--very feature rich (which I totally dig), but it wasn't nearly as light as xcompmgr.

Using xfce isn't a bad idea.  But I'm just finally getting comfortable with gnome--I hate to move to something else till I really get comfortable (bored) with gnome.  

E17 is dang cool.  If/when it's ever released, I'm totally moving that way.  It's a lot better than it used to be, but the lack of a well-integrated file manager is keeping me away at this point.

---

### Post by hyperair on 2007-09-18
Agreed. I just tried E17 yesterday.. It's mad. But I can't seem to find the Compositing module from where I installed it. There are a few features missing that keeps me in GNOME with Compiz Fusion though.

---

### Post by crazybilly on 2007-09-18
mmm...e17.  I'll be glad when that crap is done.

---

### Post by hyperair on 2007-09-18
Heh yeah. I think it's mostly incomplete for the moment.. not enough for full time use just yet =\

---

