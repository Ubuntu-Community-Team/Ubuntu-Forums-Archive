---
title: "Installing KDE themes"
date: 2005-08-29
forum: Desktop Environments
---

### Post by jsac on 2005-08-29
sup every1! first post of many im sure with the way its been going :>
anywho.... im trying to install a diff theme as the default is searing my eyes.... my prob is when i follow the install instructions:

"Download and unzip the theme archive. 
Put the theme folder in ~/.kde/share/apps/kdm/themes 
Edit your ~/.kde/share/config/kdm/kdmrc 
Change or add the line Theme=~/.kde/share/apps/kdm/themes/"THEMENAME" 
Restart KDE 
Have fun! :-) "

I dont have a "~/.kde/share/apps/kdm/themes " folder to begin with? lol
any ideas? if it helps heres the theme im tryin to install:
[http://www.kde-look.org/content/show.php?content=26718](http://www.kde-look.org/content/show.php?content=26718)

TIA!!

---

### Post by masteryoda on 2005-08-29
Welcome... 
I had the same problem... but realized that those instructions are not for us..
 for us..
1) put theme folder in  /usr/share/apps/kdm/themes
2) edit         /etc/kde3/kdm/kdmrc
3)Change or add the line Theme=/usr/share/apps/kdm/themes/"THEMENAME"
Restart KDE 
Have fun!  :)

---

### Post by jsac on 2005-08-29
thanks for the reply.... after u replied i knew that their wasnt something wrong just a diff file structure... i dropped the theme into the thememanager fodler.... then opened up theme manager control center and applied it from their... worked great.
thanks again!

---

