---
title: "Installed kde want to change back to gnome..."
date: 2005-04-03
forum: Desktop Environments
---

### Post by Melhisedek on 2005-04-03
Hi mates,
well I was installing all kind of things kde included and while installing I've got this question, what window manager I want to use. I choose kde (wanted to see how it looks) well now I get Kde startup screen but when I log in I get old gnome look (bars at top and bottom and brown kind of thing :) )
Anyway when I try to turn off the computer I only have option to "log out" which takes me back to startup screen again (where you log in) and there I can log out...
Any way of turning back to gnome or adding a button for shutdown in "system" menu again?

P.S. Using 5.04 Ubuntu...

---

### Post by ubuntu_demon on 2005-04-03
sudo dpkg-reconfigure kdm

and change your display manager to kdm(instead of gdm). This will generate shutdown/restart options in KDE and it will also change your login screen. If you login to gnome shutdown/restart will be removed there. This has technical reason.

For uninstall of KDE look here (next time do a search on the forums for this first):

[http://www.ubuntuforums.org/showthread.php?t=22697](http://www.ubuntuforums.org/showthread.php?t=22697)
[http://www.ubuntuforums.org/showthread.php?t=22652](http://www.ubuntuforums.org/showthread.php?t=22652)

---

### Post by Melhisedek on 2005-04-03
[QUOTE=demon666_nl]sudo dpkg-reconfigure kdm

and change your display manager to kdm(instead of gdm). This will generate shutdown/restart options in KDE and it will also change your login screen. If you login to gnome shutdown/restart will be removed there. This has technical reason.

For uninstall of KDE look here (next time do a search on the forums for this first):

[http://www.ubuntuforums.org/showthread.php?t=22697](http://www.ubuntuforums.org/showthread.php?t=22697)
[http://www.ubuntuforums.org/showthread.php?t=22652](http://www.ubuntuforums.org/showthread.php?t=22652)[/QUOTE]
 I'm sorry it's pretty hard for me to articulate what I need exactly. Thing is I didn't want to uninstall Kde, just get that "turn off computer" button back to system menu (under log off). I fixed it now (I think) I defaulted it to Kde and now I got the "turn off computer" back :) 

Thank you for your time!

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=Melhisedek]I'm sorry it's pretty hard for me to articulate what I need exactly. Thing is I didn't want to uninstall Kde, just get that "turn off computer" button back to system menu (under log off). I fixed it now (I think) I defaulted it to Kde and now I got the "turn off computer" back :) 

Thank you for your time![/QUOTE]
 np :)

---

