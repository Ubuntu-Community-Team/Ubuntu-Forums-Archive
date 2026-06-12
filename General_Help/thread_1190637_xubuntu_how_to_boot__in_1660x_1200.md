---
title: "xubuntu how to boot  in 1660x 1200  ?"
date: 2009-06-18
forum: General Help
---

### Post by n45w73 on 2009-06-18
Usually I boot my old pc with xubuntu without keyboard, mouse and monitor...

It boot without problem and start vnc right away...

My only problem is it allways goes to scren default resolution 800 x 600...  is there a way to force the vid card to 1600x 1200 ? 

:P

EDIT  oppss you should read 1600 x 1200 in the title of course

---

### Post by clonne4crw on 2009-09-28
Edit your /etc/X11/xorg.conf file. Under the monitor section. Remove the modes that you don't want to see. You're will be different than mine, so I can't tell you exactly what to change. Just be sure to make a backup if something goes bad.

---

