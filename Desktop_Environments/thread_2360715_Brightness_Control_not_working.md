---
title: "Brightness Control not working"
date: 2017-05-07
forum: Desktop Environments
---

### Post by joostb on 2017-05-07
I just updated to ubuntu 17, and started using Gnome, but the brightness control is not working. 

I have a Lenovo y500 with a nvidia GeForce GT 750M. 

I tried following another fix, but these didn't work for me, unfortunately. 

I created a /etc/X11/xorg.conf using sudo nvidia-settings. And added 
```
 [COLOR=#000000][FONT=&amp]Option "RegistryDwords" "EnableBrightnessControl=1"
[/FONT][/COLOR]
```
to the device section.

[COLOR=#000000][FONT=&amp]I think i should note that that the brightness icon does show up, when I press the function keys (fn + Up).

Edit: I can change the brightness using xbacklight, so I guess the question now is: how can I bind the gnome-brightness to the actual brightness

Please help
[/FONT][/COLOR]

---

