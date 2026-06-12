---
title: "application desktop icon hover"
date: 2023-12-05
forum: Desktop Environments
---

### Post by hei17 on 2023-12-05
I'm using Ubuntu 22.04 LTS gnome 42.9. When I click the Show Applications icon in the dock I go to the application desktop. I changed the default background from black to an image. An the text color from white to red, to show in my background image. In ~/.themes/mytheme/gnome-shell/gnome-shell.css ##overviewGroup { background-image: url("1992.jpg"); } #, .overview-icon {color: #ff0000; }#  
I would like to on mouse-over icon, hover, to change the hover background-color:transparent to a color that would hilite icon and the icon text. Need to be guided to the file where I can make the change. Grateful for any help!

---

### Post by hei17 on 2023-12-17
If you add this code  #.app-well-app:hover .overview-icon, .grid-search-result:hover .overview-icon {
  background-color: your color;
  border: 2px solid your color; }# to ~/.themes/mytheme/gnome-shell/gnome-shell.css. It will generate the color around the icon and text when you mouse off the icon.

---

