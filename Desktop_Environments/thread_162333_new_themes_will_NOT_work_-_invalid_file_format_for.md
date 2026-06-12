---
title: "new themes will NOT work - invalid file format for ALL themes"
date: 2006-04-18
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-04-18
I have just installed Breezy yet again (dont ask how many times ive lost count lol) and with this install and the last I cannot get any new theme working unless it is install from synaptic. I really what to use some metacity and gtk2 ones from gnome-look but I just get Invlaid File Format from any theme no matter how I try to install them. Can someone please tell me what I am missing. Is there some major Gnome file I have not updated or installed?

Any help much appreciated.

Ironfistchamp

---

### Post by aysiu on 2006-04-18
There are two types of .tar.gz files you get from [http://www.gnome-look.org](http://www.gnome-look.org)

One is a .tar.gz of a theme (window borders or controls) or icon set or login screen.

Another is a .tar.gz of a complete theme set (that one .tar.gz has folders full of window borders, controls, icons, login screens, wallpapers, etc.).

The first can be dragged and dropped to the Theme Manager window. The second cannot and must be manually untarred, and the folders within must be manually copied to the appropriate places.

It sounds to me as if you're somehow gravitating toward the second kind.

Just to be sure, though, try [dragging and dropping this theme](http://www.gnome-look.org/content/show.php?content=20972). If it works, it means you've been somehow finding only the second kind. If it doesn't, something's wrong with your Gnome Theme Manager.

---

### Post by ironfistchamp on 2006-04-19
I tried to download that but I can't seem to get the file. Think the site is broken (the authors not Gnome-Look). Have you got any other drag and drops?

Also how do you install ones you cant drag and drop?

Thanks

Ironfistchamp

---

### Post by aysiu on 2006-04-19
[QUOTE=ironfistchamp]I tried to download that but I can't seem to get the file. Think the site is broken (the authors not Gnome-Look). Have you got any other drag and drops?[/quote] Maybe [this one](http://www.gnome-look.org/content/show.php?content=37318)?

> 
Also how do you install ones you cant drag and drop? Double-click no the .tar.gz. Click "Extract." In the newly extracted folder, see what parts are in there. If there are metacity or Gtk themes, copy them to /home/ironfistchamp/.themes (.themes is a hidden directory--just press Control-H in Nautilus to see it). If there are icon themes, copy them to /home/ironfistchamp/.icons. GDM themes would go in /usr/share/gdm/themes

---

### Post by ironfistchamp on 2006-04-19
Wahey genius. I guess I was just really unlucky with my theme picking. Thanks very much. 

I must be the unluckiest guy when it comes to linux. You wouldn't believe the toubles Iv'e had getting this far. I'm thinking of publishing my story :p ....well on the net anyway.

Thanks again 

Ah I love posting here. You people seem to get the job done.

Ironfistchamp

---

### Post by phorque on 2006-04-20
hmmm... I tried OrangoTango 0.0.4 (icons) in every one of those ways but it still won't appear or install... any ideas?

---

### Post by aysiu on 2006-04-20
[QUOTE=phorque]hmmm... I tried OrangoTango 0.0.4 (icons) in every one of those ways but it still won't appear or install... any ideas?[/QUOTE] Can you provide a link to the theme?

---

### Post by phorque on 2006-04-21
[http://xoomer.virgilio.it/bat/orango-tango/](http://xoomer.virgilio.it/bat/orango-tango/) <--- it's here

---

### Post by r41nz0r on 2008-01-01
> **aysiu said:**
> Maybe [this one](http://www.gnome-look.org/content/show.php?content=37318)?

 Double-click no the .tar.gz. Click "Extract." In the newly extracted folder, see what parts are in there. If there are metacity or Gtk themes, copy them to /home/ironfistchamp/.themes (.themes is a hidden directory--just press Control-H in Nautilus to see it). If there are icon themes, copy them to /home/ironfistchamp/.icons. GDM themes would go in /usr/share/gdm/themes

Very Helpful! Thanks for the needed support I look forward to installing some elegant themes:)

---

### Post by mcduck on 2008-01-01
> **phorque said:**
> hmmm... I tried OrangoTango 0.0.4 (icons) in every one of those ways but it still won't appear or install... any ideas?

After installing thetheme, when you go to System/Preferences/Appearance you need to click the Customize-button to select individual GTK-, Metacity- and icon themes. The main Appearance-window only shows complete themes (which have settings for all of these) and individual theme components are not shown. After you have selected the different themes you want to use for icons and other stuff you can click the Save As-button in the Appearance-window to save your complete theme. After that it will show in the first window as well.

---

