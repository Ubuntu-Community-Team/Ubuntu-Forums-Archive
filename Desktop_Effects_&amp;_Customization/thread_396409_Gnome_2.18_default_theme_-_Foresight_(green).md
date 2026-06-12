---
title: "Gnome 2.18 default theme - Foresight (green)"
date: 2007-03-29
forum: Desktop Effects &amp; Customization
---

### Post by anzevi on 2007-03-29
Hi!

I really like the live new 2.18 default Gnome theme - [Foresight]("http://www.gnome.org/start/2.18/notes/en/").

I've made a complete package of that theme for you to just drag-n-drop into themes and enjoy. Wallpaper is also available.

But before I upload it, I need to know that I'm not violating any right by doing this (note that theme is taken from Gnome 2.18 vmware image). Just want to make sure :)

Thanks!

Anze

---

### Post by justin whitaker on 2007-03-29
> **anzevi said:**
> Hi!

I really like the live new 2.18 default Gnome theme - [Foresight]("http://www.gnome.org/start/2.18/notes/en/").

I've made a complete package of that theme for you to just drag-n-drop into themes and enjoy. Wallpaper is also available.

But before I upload it, I need to know that I'm not violating any right by doing this (note that theme is taken from Gnome 2.18 vmware image). Just want to make sure :)

Thanks!

Anze

It's the default theme from Gnome right? If so, it should be GPL'd...as long as you pass the package back to them, there should not be any problem.

---

### Post by anzevi on 2007-03-29
> **justin whitaker said:**
> It's the default theme from Gnome right? If so, it should be GPL'd...as long as you pass the package back to them, there should not be any problem.

It's actually Foresight's default theme. Not sure if I can upload it here, since this theme is nowhere to be found?!

---

### Post by justin whitaker on 2007-03-29
> **anzevi said:**
> It's actually Foresight's default theme. Not sure if I can upload it here, since this theme is nowhere to be found?!

If it is Foresight's theme, better make sure you have the ok to post it. I'm pretty sure they won't care, but you never know. Some people are picky about how their themes are passed around, and it may be copyrighted.

---

### Post by Geert Jan on 2007-04-03
Any news on this? I really like the look of the green Foresight theme as well.

In another thread someone said that it would be available in Feisty by default. So that is not true then I guess?

---

### Post by epimer on 2007-04-07
> **Geert Jan said:**
> Any news on this? I really like the look of the green Foresight theme as well.

In another thread someone said that it would be available in Feisty by default. So that is not true then I guess?

The Foresight GTK theme is available in their repos [here]("http://www.rpath.org/rbuilder/repos/foresight/troveInfo?t=gtk-theme-foresight"), and there's also a Murrina engine variant available on Gnome-Look [here]("http://www.gnome-look.org/content/show.php/MurrinaForesight?content=55808").

As for the wallpaper, I just took it from the Gnome 2.18/Foresight LiveCD - but then I lost it in a format, d'oh.

---

### Post by oomingmak on 2007-04-07
> **Geert Jan said:**
> I really like the look of the green Foresight theme as well.
Me too 

:grin:

---

### Post by loko on 2007-04-09
foresight-green looks really nice, but if i select it, synaptic looks like really bad.

can somebody confirm this and is there a workaraound?

---

### Post by gamma on 2007-04-21
> **loko said:**
> foresight-green looks really nice, but if i select it, synaptic looks like really bad.

can somebody confirm this and is there a workaraound?
Not sure if that's a bug or a "feature," but Synaptic is run as root so the theme needs to exist for the root user.

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons

That will make a link to your current (user) themes for the root user.

---

### Post by loko on 2007-04-23
thank you for this solution

---

### Post by Azrael Nightwalker on 2008-01-02
The Foresight Green Gnome (GTK) Theme can be found here: [http://art.gnome.org/themes/gtk2/1345](http://art.gnome.org/themes/gtk2/1345)
And the wallpaper can be downloaded from here:
[http://www.rpath.com/rbuilder/repos/foresight/files?t=gnome-backgrounds;v=/foresight.rpath.org%40fl%3A1-devel//1/1190088548.670%3A2.20.0-2-1;f=5%23use%3A%7E%21builddocs](http://www.rpath.com/rbuilder/repos/foresight/files?t=gnome-backgrounds;v=/foresight.rpath.org%40fl%3A1-devel//1/1190088548.670%3A2.20.0-2-1;f=5%23use%3A%7E%21builddocs)

---

### Post by chrisccoulson on 2008-01-02
> **gamma said:**
> Not sure if that's a bug or a "feature," but Synaptic is run as root so the theme needs to exist for the root user.

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons

That will make a link to your current (user) themes for the root user.

A neater way of doing it is to actually install the theme globally in /usr/share/themes.

---

