---
title: "GDM Login"
date: 2005-05-03
forum: Desktop Environments
---

### Post by benson on 2005-05-03
can someone help me customize my login? I want to remove the LANGUAGE & SESSION in the login screen. Only USERNAME would appear. what file do i need to edit? thanks!  :razz:

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=benson]can someone help me customize my login? I want to remove the LANGUAGE & SESSION in the login screen. Only USERNAME would appear. what file do i need to edit? thanks!  :razz:[/QUOTE]


sounds like you want xdm

sudo apt-get install xdm

---

### Post by Alexander Kirillov on 2005-05-04
[QUOTE=benson]can someone help me customize my login? I want to remove the LANGUAGE & SESSION in the login screen. Only USERNAME would appear. what file do i need to edit? thanks!  :razz:[/QUOTE]
 The look of login screen is determined by gdm theme. You can look for a new gdm theme (many themes are available here: [http://art.gnome.org/themes/gdm_greeter/)](http://art.gnome.org/themes/gdm_greeter/)), or you can modify the existing one. It is described in the file
/usr/share/gdm/themes/<themename>/<themename>.xml

You can manually edit this file (if you are certain you can produce a valid xml file), commenting out all items relevant to SESSION and LANGUAGE entires. Keep a backup - just in case...

---

### Post by jimcooncat on 2005-05-04
Url correction for parent post, an extra closing parenthesis fouled the clickability.

[http://art.gnome.org/themes/gdm_greeter/](http://art.gnome.org/themes/gdm_greeter/)

---

### Post by benson on 2005-05-04
thank you guys!   :-)

---

### Post by benson on 2005-05-09
[QUOTE=Alexander Kirillov]The look of login screen is determined by gdm theme. You can look for a new gdm theme (many themes are available here: [http://art.gnome.org/themes/gdm_greeter/)](http://art.gnome.org/themes/gdm_greeter/)), or you can modify the existing one. It is described in the file
/usr/share/gdm/themes/<themename>/<themename>.xml

You can manually edit this file (if you are certain you can produce a valid xml file), commenting out all items relevant to SESSION and LANGUAGE entires. Keep a backup - just in case...[/QUOTE]

thanks for this. :D but i change my mind. messing with this file (human.xml) would render my OS unusable. i must learn some XML programming language first.  ](*,)

---

### Post by Alexander Kirillov on 2005-05-09
[QUOTE=benson]thanks for this. :D but i change my mind. messing with this file (human.xml) would render my OS unusable. i must learn some XML programming language first.  ](*,)[/QUOTE]
This is a prudent decision. 

But as I do know a bit XML, I tried editing this file to remove "session" and "language" items. I tested the result and it works. So try overwriting /usr/share/gdm/themes/Human/Human.xml with the acttached file  (first making a backup copy of the original file!). The file name should be Human.xml (capitalization matters!) - I had to rename it to Human.txt, otherwise the forums software would not accept upload. 

Let me know if it works for you.

---

### Post by benson on 2005-05-11
Cool! it worked perfectly. Thanks for the *Human.txt* :)

---

