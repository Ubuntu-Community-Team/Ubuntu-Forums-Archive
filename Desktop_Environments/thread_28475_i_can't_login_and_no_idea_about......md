---
title: "i can't login and no idea about....."
date: 2005-04-20
forum: Desktop Environments
---

### Post by Skaman on 2005-04-20
when i enter my psw in the login panel i got a black screen and then get back to the login panel again......
here is the putput of startx in prompt mode....
do anybody have any idea of what this could be....???
[IMG]http://osc4r.altervista.org/Img/krash.JPG[/IMG] 
i don't think is a xorg.conf problem coz my xorg.conf file worked well till now....
i had this problem rebooting after trying to configure my mouse buttons with imwheel

---

### Post by Skaman on 2005-04-20
[http://RAFB.NET/paste/results/sU9HTX46.html](http://RAFB.NET/paste/results/sU9HTX46.html)

here the Xorg  log

---

### Post by Tiede on 2005-04-20
If it recognize your mouse, X probably won't start (I had this problem with Debian Woody on an old laptop)
You should try enabling the option that let X start with or without mouse.. I think it might be LOADFAIL, but I cannot remember. 'twas so long ago...

---

### Post by quickgun on 2005-04-20
Heres a shot in the dark: try using the ati module provided by X.org.  I'm seeing some drm device errors in there.

---

