---
title: "kde file associations under gnome"
date: 2010-01-08
forum: Desktop Environments
---

### Post by wgw on 2010-01-08
I have a kde application (Basket Notes) that is supposed to launch applications according to file associations. Unfortunately it does not seem to be following Gnome associations (when I look at them through Nautilus or run them from Nautilus); I'm assuming that KdeInit is using other file association than Gnome. When I thy to launch a pdf file, I get "Could not find 'kompozer' executable.": it is trying to open the html editor kompozer, which doesn't make any sense. Under gnome, evince opens pdf files. 

What are the files that kdeInit uses for file associations _under gnome!_

Thanks in advance for any pointers. (I may have to install all of KDE just to fix this, but I'll try to find a more direct solution....)

---

### Post by wgw on 2010-01-08
I think I found it in the .desktop files here: ~/.local/share/applications

Had to clean up the links there.

---

