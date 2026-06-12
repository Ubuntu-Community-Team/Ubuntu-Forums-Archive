---
title: "Questions about KOffice"
date: 2005-12-11
forum: General Help
---

### Post by idtt2s on 2005-12-11
Question 1:
                  Why does KOffice (KWord) need gtk/gconf to be installed?

Question 2:
                  I deleted the KOffice menu entries, removed KOffice, installed KOffice. How do I get the icons back?

---

### Post by aysiu on 2005-12-11
[QUOTE=idtt2s]Question 1:
                  Why does KOffice (KWord) need gtk/gconf to be installed?[/quote] It doesn't.

> 
Question 2:
                  I deleted the KOffice menu entries, removed KOffice, installed KOffice. How do I get the icons back? Right-click on the KMenu, Edit Entries.

---

### Post by korkow on 2005-12-11
I would reccomned just using OpenOffice...

---

### Post by aysiu on 2005-12-11
[QUOTE=korkow]I would reccomned just using OpenOffice...[/QUOTE] Because it easily imports and edits PDF files? It really depends on what you want to do. KOffice, GnomeOffice, and OpenOffice each has its own strengths.

---

### Post by idtt2s on 2005-12-11
> It doesn't.
```

root@ubuntu:/home/ming# apt-get remove gtk*
The following packages will be REMOVED:
  gconf2 koffice kword libgconf2-4 libgsf-1 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libwv2-1c2
0 upgraded, 0 newly installed, 9 to remove and 88 not upgraded.
Need to get 0B of archives.
After unpacking 35.4MB disk space will be freed.
Do you want to continue [Y/n]?   

```

> Right-click on the KMenu, Edit Entries.
I asked because I wanted to avoid adding the entries manually.

---

### Post by aysiu on 2005-12-11
This is a list of KWord and all its dependencies:
[http://packages.ubuntu.com/breezy/kde/kword](http://packages.ubuntu.com/breezy/kde/kword)

Not a Gtk in sight.

Why do you want to unintall Gtk*, anyway?

My guess is that you can uninstall it and then reinstall KOffice. If KOffice really needs Gtk (and you really need KOffice), Gtk will be reinstalled. And uninstalling KOffice won't lose any of your settings.

---

### Post by idtt2s on 2005-12-11
```

root@ubuntu:/home/ming# apt-get remove koffice*   
  
root@ubuntu:/home/ming# apt-get remove gtk*     
 
root@ubuntu:/home/ming# apt-get install koffice
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gconf2 karbon kchart kformula kivio koffice-data koffice-libs koshell
  kpresenter krita kspread kugar kword libgconf2-4 libgsf-1 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libwv2-1c2
Suggested packages:
  koffice-doc-html koffice-i18n koffice-dev wordnet tetex-extra
Recommended packages:
  openoffice.org-mimelnk kghostview libkscan1
The following NEW packages will be installed:
  gconf2 karbon kchart kformula kivio koffice koffice-data koffice-libs
  koshell kpresenter krita kspread kugar kword libgconf2-4 libgsf-1
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libwv2-1c2
0 upgraded, 20 newly installed, 0 to remove and 88 not upgraded.
Need to get 0B/26.3MB of archives.
After unpacking 78.6MB of additional disk space will be used.
Do you want to continue [Y/n]?    

```
Speaks for itself!

Also, the main issue is regarding menu entries!

---

### Post by aysiu on 2005-12-11
[QUOTE=idtt2s]
Also, the main issue is regarding menu entries![/QUOTE] And it takes you longer to manually make menu entries for that than to type those posts?

Hm. I don't know. In Gnome, you can do *killall gnome-panel*, and that refreshes the menus. I'm not sure what you do for KDE.

---

