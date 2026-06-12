---
title: "Adding items to Gnome Applications Menu"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Mr Black on 2005-04-09
I just upgraded to Horay (5.04) final release, and I have been trying to add items to the Applications menu in Gnome.  I did some searching around and it seems that other people have had the same issues doing so as well, but all of the posts delt with one of the previous releases of Horay.  (i.e. not the final release)  I was just wondering if anyone has found out how to add items to the Applications menu.

---

### Post by Perfect Storm on 2005-04-09
Grab Gnome-editor application. Read more about it here: [http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor) make sure that your repositories have enable universe etc.

---

### Post by nharihar on 2005-04-09
[QUOTE=Mr Black]I just upgraded to Horay (5.04) final release, and I have been trying to add items to the Applications menu in Gnome.  I did some searching around and it seems that other people have had the same issues doing so as well, but all of the posts delt with one of the previous releases of Horay.  (i.e. not the final release)  I was just wondering if anyone has found out how to add items to the Applications menu.[/QUOTE]
 Same here, upgraded to Hoary from Warty and cant add item to Gnome Apps Menu, anybody know of a way to - please let us know.

---

### Post by Mr Black on 2005-04-09
Thanks Artificial Intelligence. I had just found that link and was comming back to post it.  It works great. Plus I'm glad to see they changed over the guide from Warty.  I was looking for it yesterday after I had upgraded.

---

### Post by Perfect Storm on 2005-04-09
Just a little warning Gnome-editor is a bit bugged, so carefull how you use it.

---

### Post by nickx on 2005-04-09
[QUOTE=Artificial Intelligence]Just a little warning Gnome-editor is a bit bugged, so carefull how you use it.[/QUOTE]
 Hopefulle there will be a stable version soon. I f my menu by deleting things "i have now 2 application menus" anyone know how to get the menu fixed by default settings?

---

### Post by Perfect Storm on 2005-04-10
Hmmm...try with:

goto 

cd /home/orion/.config/menus

before deleting 'applications.menu' make a backup of it. Logout & login if nothing changed.

---

