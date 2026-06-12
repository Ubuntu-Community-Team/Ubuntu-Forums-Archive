---
title: "xfce themes"
date: 2006-11-13
forum: Desktop Environments
---

### Post by tater_3001 on 2006-11-13
Does anyone kno how to add more themes to the xfce user interfac? I looked on the xfce site and it doesnt help newbs like me very much. Ha Thanks Turner

---

### Post by lonce on 2006-11-13
go to gnome-look.org and download what ever you would like.  Then in XFCE go to the place where it lets you choose your skin.  I cant remember where off the top of my head.  Then you just click on add theme, or install theme and point it towards the tar file.  Should work.  I am not sure if drag and drop works for that in XFCE.

---

### Post by je m'ennuie on 2006-11-13
There is no "add theme" or "install theme" in XFCE "user Interface settings". 
You can add themes this way :
Open Thunar
In your user directory create a new hidden folder called ' .themes'
download a theme from xfce-look.org
Right click on it and 'extract to' /home/tater/.themes *(there is an option to show hidden folders)*
The downloaded theme will now show up in user interface settings
You can do the same with icons themes with a ' .icons' folder

---

### Post by tater_3001 on 2006-11-13
OMG THANK YOU SOOO MUCH, Turner

---

### Post by tater_3001 on 2006-11-14
haha well after several attempts i hate to say that it still didnt work haha thanks anyway, Turner

---

### Post by je m'ennuie on 2006-11-14
What themes did you try with ?

---

### Post by tater_3001 on 2006-11-14
haha i figured it out heres how i did it
 
 When you download new window manager styles, they usually come in a .tar or .zip archive. Extract the contents, and do:

sudo cp -r folder-with-new-theme /usr/share/themes/

haha i looked on the xubuntu site :P haha

---

### Post by videodrome on 2006-11-14
Ha. Gooooood luuuuck with this! Especially if you are trying to change the icons for the xfce settings and the various applets. 

The mixer icon for example. In the last release of xfce it was messed up and became a cup with pens and pencils in it. Now, with 4.4 rc2 it's a whistle. Go figure. Seemingly sometimes Xfce uses random indecipherable icons from the hi-color directory wherever it chooses, and who knows how to change them. Othertimes it just bugs out and screws up half of the menu icons if you dare try to install a new icon theme.

Loomis

---

