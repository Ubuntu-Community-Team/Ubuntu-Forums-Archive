---
title: "Resize topbar in Gnome"
date: 2016-08-15
forum: Desktop Environments
---

### Post by poumon on 2016-08-15
Hello everyone, i use ubuntu gnome 16.04. I really like that but i found the topbar too big. I ask if there is a way to make it smaller ? An extension or a file to edit ? 

Thank you :)

---

### Post by Joentokyo on 2016-08-15
I am not sure if it is the same as on my system. I use gnome fall back or flashback, but if it is the same try holding down the alt key while right clicking the bar and select properties. That should open up a graphic  that lets you change the size by increasing the number of pixels.

---

### Post by poumon on 2016-08-15
Yes but we can't do that with the new version of Gnome. But i found a solution ! I modified the usr/share/themes/name-of-the-theme/gnome-shell/gnome-shell.css file

We have to found 

> 
/* Panel */

#panel {
    background-gradient-direction:none;
    background-color: rgba(0,0,0,0.5);
/*    border: 0px solid rgba(90,105,111,0.5);
    box-shadow: 0px 0px 0px 1px rgba(0,0,0,0.15);*/
    border: 1px solid rgba(90,105,111,0.5);
    box-shadow: 0px 1px 3px 1px rgba(0,0,0,0.5);
    border-top:0px;border-right:0px;border-left:0px;
    font-weight: bold;
    height: 24px;}
  
we have to change the " height " value. After we have to reload the theme. I use the extension " activities configurator " for the other parameters of the topbar ( sorry for my English )

---

