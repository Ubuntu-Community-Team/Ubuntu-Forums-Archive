---
title: "Weird Ooffice display problem under gnome"
date: 2006-01-17
forum: Desktop Environments
---

### Post by casfindad on 2006-01-17
I am running ubuntu and kubuntu on my desktop, and I recently noticed a display issue when running OpenOffice (v. 1.9.129-01) under gnome. When I start any Ooffice application in gnome, I find that half or more of the toolbar buttons do not display. If I move my cursor over the empty toolbars, I can see the buttons appear, but each disappears again as my cursor moves on. The menu behavior is similar. Most of the menu headings appear when I start Writer (or Draw, Impress, etc.), but they all disappear as soon as I click on a menu heading. The drop down will be blank, but individual menu entries will show up as I move the cursor down the column. I eventually found that removing openoffice.org2-gnome solves the problem, but of course I don't have the nice gnome theme as the Ooffice interface then.

When I run Ooffice in kde, no problems.

Any suggestions?

casfindad

P.S. In case it's germaine, I should say that I had previously installed OpenOffice v. 2.0.1 using Automatix. I don't know if this problem was happening under 2.0.1 as I was working in kde, but I had to uninstall that version when I found several bugs re: templates had shown up in the latest version of Ooffice. I completely (I think) removed that version, then re-installed 1.9.129.

P.P.S. On a related note (which I'll post in a separate thread), I'm noticing that the smeg menu editor is not working either. Thought I mention it just in case it's related.

---

### Post by Psy-Q on 2006-02-02
I have the same problem, but the other way round. Disappearing buttons in KDE but not in Gnome. I've never tried Automatix, so I still have Ubuntu's default install of OOo.

I noticed the problem disappears when I disable "Use my KDE style in GTK applications" and choose a specific style using the KDE control center. Using the Human style for example makes things work again.

The "GTK styles and fonts" item in kcontrol appears only when gtk2-engines-gtk-qt is installed.

---

