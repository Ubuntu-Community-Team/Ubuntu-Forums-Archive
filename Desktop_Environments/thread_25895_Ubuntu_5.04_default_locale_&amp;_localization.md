---
title: "Ubuntu 5.04 default locale &amp; localization"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Vertical on 2005-04-11
Hello
Just installed ubuntu 5.04 and some questions arrived  \\:D/ 

- What is default locale for ubuntu? During installation I choose ru_RU.KOI8-R and now my GNOME enviroment is 50/50 localized  :| . Maybe I should select ru_RU.UTF8? 

-  can't run synaptic & "Add/remove programs". When I launch synaptic, it asks me for the password. I type root password (correct) and it says that it is wrong! For 'su' command this pass is correct. Also my user password doesn't make synaptic to start. What's that?  :---) 

- How to add fonts to my GNOME? In kde there is an option in 'KDE kontrol panel', which gives me ability to easily install fonts. Any alternatives in GNOME?

Thanks

---

### Post by njs12345 on 2005-04-11
Did you activate the root account with `sudo passwd`? If you did, that might be what's stopping gksudo from running Synaptic, I don't know..

Hoary is meant to use Unicode anyway, and it rules (;)), so it might be better if you used it. Use `sudo dpkg-reconfigure locales` and select ru_RU.utf8

I think you might need to install a language pack or something to enable additional languages, but I'm not sure.. I'm English so I don't need i18n.

To install fonts, move them to ~/.fonts/ :)

---

### Post by lao_V on 2005-04-11
[QUOTE=Vertical]Hello

- can't run synaptic & "Add/remove programs". When I launch synaptic, it asks me for the password. I type root password (correct) and it says that it is wrong! For 'su' command this pass is correct. Also my user password doesn't make synaptic to start. What's that? :---) 

[/QUOTE]

Synaptic is launched with gksudo which means you need to enter YOUR password! If you want to use it using root (su) then first enable the root by typing "sudo passwd root" and then modify the menu to use gksu instead of gksudo

---

### Post by Vertical on 2005-04-11
Thanks
But I still have troubles with i18n and localization. I read guide for ubuntu, tried commands you adviced. I just want to be able to start synaptic from regular user, selecting it from GNOME menu. the only way I can start synaptic now from regular user  is to run it from terminal after 'su' command, but this way is not really useable..
Also, I want to be able login from GDM with my root account.

---

