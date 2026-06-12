---
title: "I cant choose pekwm from gdm"
date: 2005-06-13
forum: Desktop Environments
---

### Post by waft on 2005-06-13
I installed pekwm but it wasnt added to session menu in gdm. how can I add it to there?

---

### Post by Juippisi on 2006-03-12
I think this works with GDM too. This is how I added it to my KDM-list:

cd /usr/share/xsessions/
sudo vim pekwm.desktop
----------
[Desktop Entry]
Encoding=UTF-8
Name=PekWM
Comment=Log in using PekWM (Version 0.1.4)
Type=XSession
Exec=/usr/bin/pekwm
TryExec=/usr/bin/pekwm
----------

just change the paths.

---

### Post by tript on 2006-06-03
I've tried creating that file in the sessions dir...isn't working for me.  I've spent quite a bit of time on this, so I registered here to seek help.

Could someone point me to the next step they would suggest? Upon request, I'll post ~/.xsession and/or whatever else you would want to see.  Time for food. :)

thanks
tript

PS: does putting type=Application make a difference?

---

