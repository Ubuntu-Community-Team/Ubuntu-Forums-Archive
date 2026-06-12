---
title: "Cairo-Clock Position"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by Elrian on 2008-02-28
Hello,

I installed Cairo-Clock but it doesn remeber its position every time i reboot my computer...

Anyway to fix this?

Also i wanted to try to edit the config file manually but how do i know its screen position coordinates?

Thanks for tour replies!

---

### Post by ajeetraj on 2008-02-28
which version of cairo-dock are you using? if you are using 1.5...then it has a lot of bugs. Try to stick with 1.4 at the moment which is very stable right now. you can get the deb packages from here: 
[cairo dock deb files]("https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108")

Just keep in mind when you have cairo-dock installed already, after you remove it (you can remove it just from the terminal by : sudo apt-get remove cairo-dock) you should go to your /home/<username> folder and press CTRL + h and then you will see all the configuration files. just look for ".cairo-dock" and then just delte that folder. 

If you install after that then you should get your 1.4 working. also try to get both of the .deb packages...the main installation package and the plugins. after installing both then run cairo-dock and you will be ok. 

hope this helps!

---

### Post by Elrian on 2008-02-28
Thanks for your reply but i was talking about Cairo-Clock not Cairo-Dock...

---

### Post by Nythain on 2008-02-28
you can tell it dimensions and position via command line... and if you are autostarting it, just add the arguments to the autostart entry... or write a simple script to launch it... you can man it im sure, or google it, to get all the command line options

---

