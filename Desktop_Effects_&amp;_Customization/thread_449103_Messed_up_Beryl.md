---
title: "Messed up Beryl"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by squeezy on 2007-05-19
I have Beryl set to automatically come on when  I login in. I did something, and now when Beryl loads everything goes white, except whatever effects I have on, and Cube shows all white, except for the red Beryl picture on the top and bottom of the Cube.

I have tried booting into Failsafe Gnome, but Beryl still loads automatically, and prevents me from disabling it.

Now I'm stuck, can anyone help?

---

### Post by Ub1476 on 2007-05-20
Uhm, I think you can uninstall Beryl from the terminal without need to log in. Press ALT+f2 or something, maybe Control f2, not sure.:( Anyways when you are in the terminal write: 

```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
``` 

It will remove both XGL and beryl. If you are not using XGL just remove it till you come to "beryl beryl-core, etc"

---

