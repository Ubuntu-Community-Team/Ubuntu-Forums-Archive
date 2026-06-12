---
title: "OOo 2.02 theme"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Steven_B on 2006-05-31
OOo2.02 looks bad on my system.  After the upgrade to Dapper, OOo was changed somehow, so I installed the openoffice.org-* packages.  Now, the menus, etc, don't match the rest of my system theme.  None of the other apps have done this so far as I can tell.  What do I need to fix?
Along those lines, what is the difference between OOo 2.02 and the different stuff the update to dapper installed?  Are those all just metapackages?

---

### Post by gunksta on 2006-06-01
First, a couple of requests to help us help you....
[LIST]
[*]Could you please post a screenshot?
[*]Do you have KDE/Kubuntu installed on top of Ubuntu?
[*]What graphics card / driver do you have installed?
[*]Are the errors consistent when you change GNOME themes or does OpenOffice work with some themes and not others?[/LIST]
Off the top of my head, it might be a simple lack of the right package. Something might have borked in the upgrade. I would first check to see if these are installed:
openoffice.org-gnome
openoffice.org-gtk
ubuntu-desktop

Make sure you have the openoffice.org-* packages installed. You can remove the transitional packages marked openoffice.org2-*

---

### Post by Steven_B on 2006-06-01
It was just a matter of not having the openoffice.org-gnome and openoffice.org-gtk packages installed.  Thanks!

---

