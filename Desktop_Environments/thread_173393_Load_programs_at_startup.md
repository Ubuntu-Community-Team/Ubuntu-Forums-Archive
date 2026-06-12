---
title: "Load programs at startup?"
date: 2006-05-10
forum: Desktop Environments
---

### Post by Paradoxx on 2006-05-10
Hi 

I finally got my wireless netcard running on Linux :D

I'm running Ubuntu brezzy 5,10.

I just have one littel problem. I can't get firestarter and katalpult to run on when Ubuntu startup, i know i have to use the sessions manager... but i don't know that to write?

I've tried writing ”sudo firestarter” but that didn't seem to work.

Can anyone help me (I'm a newbie so have patient with me :P)

---

### Post by Ramses de Norre on 2006-05-10
Do you really need the firestarter gui at start up? You'll need to edit /etc/sudoers for it, and the firewall works without the gui launched so I wont start with it if you just want the firewall running.
For the other program: system > preferences > sessions > start up programs tab and add a new entry with as command the command for the program (probably its name) and as order 50.

---

### Post by depu on 2006-05-10
have a look at 
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by Paradoxx on 2006-05-10
I can't get katapult starting but just wirting "sudo katapult" 

and i can't open the file "sudoers"... I've tried open it with teksteditor and openoffice writer... but i can't open the file... ?

---

### Post by Omnios on 2006-05-10
try
```
sudo gedit /etc/sudoers 
```

---

### Post by moore.bryan on 2006-05-10
[QUOTE=Paradoxx]I can't get katapult starting but just wirting "sudo katapult" 

and i can't open the file "sudoers"... I've tried open it with teksteditor and openoffice writer... but i can't open the file... ?[/QUOTE]

*it should be "gksudo katapult" b/c when you edit the sudoers properly it'll set everything for gksu...*

---

### Post by Paradoxx on 2006-05-10
[QUOTE=moore.bryan]*it should be "gksudo katapult" b/c when you edit the sudoers properly it'll set everything for gksu...*[/QUOTE]

Yes it works... but every thing i run with katapult is "back to standart".. if i run firefox, it is the standart installation without alle my extentions and so.... but if i run firefox normal, it's all set as i use to have it ? strange...

---

### Post by moore.bryan on 2006-05-10
[QUOTE=Paradoxx]Yes it works... but every thing i run with katapult is "back to standart".. if i run firefox, it is the standart installation without alle my extentions and so.... but if i run firefox normal, it's all set as i use to have it ? strange...[/QUOTE]

*do you have more than one install of firefox?  the only thing you'd have to do is set the startup to point at the correct firefox (i.e. "gksudo /usr/local/bin/firefox" versus "gksudo firefox").*

---

### Post by Paradoxx on 2006-05-10
[QUOTE=moore.bryan]*do you have more than one install of firefox?  the only thing you'd have to do is set the startup to point at the correct firefox (i.e. "gksudo /usr/local/bin/firefox" versus "gksudo firefox").*[/QUOTE]

I'm pretty sure that i only have one firefox installation... but the same happen if i run the terminal... the defult was white background and blacktext, but i changed it to black background and white text. 
If i run the terminal with katapult, it's the defult theme that's loaded....

---

### Post by moore.bryan on 2006-05-10
*have you looked through the forum at [http://www.kde-apps.org/content/show.php?content=33985](http://www.kde-apps.org/content/show.php?content=33985) to see if there's any known bugs?*

---

### Post by Paradoxx on 2006-05-11
[QUOTE=moore.bryan]*have you looked through the forum at [http://www.kde-apps.org/content/show.php?content=33985](http://www.kde-apps.org/content/show.php?content=33985) to see if there's any known bugs?*[/QUOTE]

No i have not... but i was thinking... I'm running Ubunbu (GNOME), and katapult is made for KDE... so maby that's the problem?

---

### Post by moore.bryan on 2006-05-11
*that can make it buggy or take FOREVER to load... i use amarok (made for kde) and gnome; they just don't always get along.  what exactly are you using katapult for?  have you looked around for a gnome app which does the same thing?*

---

### Post by Paradoxx on 2006-05-11
[QUOTE=moore.bryan]*that can make it buggy or take FOREVER to load... i use amarok (made for kde) and gnome; they just don't always get along.  what exactly are you using katapult for?  have you looked around for a gnome app which does the same thing?*[/QUOTE]

No i have not looked for other similar programs for GNOME... maby i should... do you know any ?

---

### Post by moore.bryan on 2006-05-11
*if you're running dapper, you already have it.  [http://digg.com/linux_unix/Screencast_of_GNOME_2.14_s_Deskbar](http://digg.com/linux_unix/Screencast_of_GNOME_2.14_s_Deskbar)*

---

