---
title: "severe KDE upgrade problems"
date: 2010-02-25
forum: Desktop Environments
---

### Post by His on 2010-02-25
I upgraded to KDE 4.4 and I had some severe crashes when I restarted. There is no desktop, no bar at the bottom, no system tray... nothing. All that there is that loads are the programs that were open the last time I ssshut down KDE... and it's super laggy.

Is there a way I can logout of KDE fffffffrom a terminal? If I canI can get into gnome and try reconfiguriiiiing things. Right the desktop manager automaticaly startes me up in KDE... which is buggy.. hence the reason or mmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmy bad bad typing... like all those m's... they just showed up... seriousssssly...

or is t way I can get into my settings that would aaaallow me         to have a choiiiiiice of whichhhh dddddesktop to log into?

---

### Post by His on 2010-02-25
Okay, I got out of it. I just did alt+f2 and typed logout. Now, I'm wondering what in the heck happened. Has anyone ever heard of something similar happening?

---

### Post by syncmasterpt on 2010-02-26
Just jump into a terminal console with ctrl-alt-F1, and login wih your credentials.

Execute 

 mv .kde .kde_old

and then

 sudo service kdm restart

and logon again.

Should be fixed.

---

