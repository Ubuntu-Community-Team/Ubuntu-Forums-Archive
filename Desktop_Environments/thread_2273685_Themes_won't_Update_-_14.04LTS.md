---
title: "Themes won't Update - 14.04LTS"
date: 2015-04-14
forum: Desktop Environments
---

### Post by louis077 on 2015-04-14
Not sure whats' going on here but I can't change to any theme besides Ambiance. I've tried multiple methods including "gsettings set......", "unity tweak", and "ubuntu-tweak". Even the default ones in the "Appearance" setting don't do anything. I don't get any errors just no results. The permissions on the /usr/share/themes folder looks good. Any suggestions? 

This is a somewhat new install and I had to switch back and forth between the US and Main server when doing all my updates so not sure if this broke something. I also installed the lightdm greeter and then switched back to the unity one, not sure if I broke something there, but my greeter works great. ;)

I also attached my output of "unity --replace". Not sure if it helps.

----------------------EDIT-------------------

Looks like the only change and nothing else. If I do env | grep GTK. I get this:

GTK_MODULES=overlay-scrollbar:unity-gtk-module
GTK_IM_MODULE=ibus


Thanks for any suggestions!

---

### Post by louis077 on 2015-04-14
i was using a custom lightdm config file to run my display script. Whatever reason it wasn't allowing the other parts of unity to load. I put the script in the 50-ubuntu.conf file instead and everything loads perfectly. After reading the [lightdm wik]("https://wiki.ubuntu.com/LightDM")i I don't agree when it says to make your config file since this will bypass the other default ones pretty much breaking stuff. Maybe someone more experienced can correct me here. Below is my old configs, along with my new 50-ubuntu.conf one.

This is the post that saved my bacon.

[http://askubuntu.com/questions/445957/is-it-normal-for-lightdm-conf-edits-to-not-affect-the-desktop-screen-resolution/446050#446050](http://askubuntu.com/questions/445957/is-it-normal-for-lightdm-conf-edits-to-not-affect-the-desktop-screen-resolution/446050#446050)

---

