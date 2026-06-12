---
title: "how to change gnome default configure in system wide?"
date: 2007-01-22
forum: Desktop Environments
---

### Post by zzw on 2007-01-22
I now want to custom gnome for my customer,  such as use only on panel instead of the default two panel ,  set default mail app to thunderbird and so on. 

where can I do this in system wide?

---

### Post by ComplexNumber on 2007-01-22
[this]("http://gnomefiles.org/app.php/pessulus") may help. you will find it in the repos.

---

### Post by zzw on 2007-01-23
thanks! 
pessulus can do it for  one computer.
 
I want to change gnome default setup , where to change theme setup in system wide? 
bucause there are two more PCs need to do it , so I want to make a deb file and spread it to every one who want to custom there gnome.

---

### Post by ComplexNumber on 2007-01-23
> where to change theme setup in system wide?i'm not too sure where the default theme is stated, bt the default icon theme is in /usr/share/icons/default/index.theme


for *most* things, you've find that the defaults for a systemwide setup are stated in various places in  the /etc directory.

---

### Post by zzw on 2007-01-23
thanks! 

> **zzw said:**
> thanks! 
where to change theme setup in system wide? 

I'm sorry for error write "the" to "theme"&#34;&#12290; 

if you want custom gnome, some custom such as theme, and background and etc. can do by modified files in /usr/share/gconf/defaults/ , and then exec  update-gconf-defaults to make you change to available. 

I want to custom gnome to: 
1) only one panel  at top, instead of two panel at top and bottom
2) set the deult browser to firefox, and set default mail client to thunderbird
3) custom applets on panel 

how to do?

---

