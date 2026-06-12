---
title: "Odd windowing system"
date: 2005-08-21
forum: Desktop Environments
---

### Post by dthsqd on 2005-08-21
I just need some help identifying what type of windowing system this is.  Now Ubuntu/Kubuntu is my first distro and I have been using it for 3 months (I am still a newb) but some programs use this very ugly windowing system (not KDE).  It looks something like this...

 [IMG]http://img.photobucket.com/albums/v244/EVNovaGuy/ugWindows.png[/IMG]

Can anyone identify what windowing system this is and how I can take this and make it look like a pretty KDE window?

EDIT: The Border and the Toolbar is KDE, but the insides are extremely ugly...

EDIT #2: Maybe I shouldn't dis the windowing system, it might offend some people who use it on a regular basis.

---

### Post by arcanistherogue on 2005-08-22
It is a Gnome program trying to use your default KDE theme.  To get it nice and pretty, do "sudo apt-get install gtk-engines-gtk-qt", then go into the Control Center and under Appearance and Themes go to the gtktheme tab.  Then, select the Gnome skin you want it to use.  I think "Clearlooks - Quicksilver" looks the best.

---

### Post by dthsqd on 2005-08-22
sudo apt-get install gtk-engines-gtk-qt

I did an apt-get but it couldn't find it.  I found gtk2-engines-gtk-qt in kynaptic so I'm guessing this is the one.

Well I got the package and set one of the themes, cept it hasn't changed anything.  Could it just be a gtk program (not gnome specific?) cause the person wanted to make his program portable?

---

### Post by AgenT on 2005-08-22
gtk2-engines-gtk-qt seems to only work on gtk2 applications. The application you are using may be gtk (as in gtk1). No idea how to change GTK applications to look like native KDE.

---

### Post by dthsqd on 2005-08-22
Kdamn (KDE damn :))

I don't wanna work with an ugly XMMS player, and I use that all the time.  I also use other apps that use GTK like ePSXe, and I've seen other people fix it, but I think they used GNOME so they didn't worry about anything.

---

### Post by dthsqd on 2005-08-22
Wow I never thought I'd find the solution myself...

there is a package called gtk-theme-switch, and although its limited, it works :)!

---

### Post by AgenT on 2005-08-22
Also, xmms comes with it's own theme engine and themes.

---

