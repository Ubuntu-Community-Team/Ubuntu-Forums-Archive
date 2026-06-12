---
title: "Hoary has no application:///"
date: 2005-02-21
forum: Desktop Environments
---

### Post by delltony on 2005-02-21
Hopefully I'm posting this in the correct forum and secondly I hope it hasn't been adressed somewhere else. If it has please pardon me for i searched with no luck before posting.  In any case how does one add items to the application menu in gnome now?  from my understanding they are now /usr/share/gnome/vfolder/whatever.directory files now    Before in warty you could just type applications:/// and then just add your launchers there. Is there still a way to do this if so please help. thanks

Update:
Problem resolved
[http://www.gnome.org/start/2.0/menuediting.html](http://www.gnome.org/start/2.0/menuediting.html)

Simple go to /usr/share/applications you might have to chmod it first to get access but once there look at one of the .desktop files as a reference i choose xchat.desktop  you will get the general idea of how it works. ass the exec=<programnamehere> and then gave it a category and thats it.

---

### Post by paul cooke on 2005-02-21
[QUOTE=delltony]Hopefully I'm posting this in the correct forum and secondly I hope it hasn't been adressed somewhere else. If it has please pardon me for i searched with no luck before posting.  In any case how does one add items to the application menu in gnome now?  from my understanding they are now /usr/share/gnome/vfolder/whatever.directory files now    Before in warty you could just type applications:/// and then just add your launchers there. Is there still a way to do this if so please help. thanks

Update:
Problem resolved
[http://www.gnome.org/start/2.0/menuediting.html](http://www.gnome.org/start/2.0/menuediting.html)

Simple go to /usr/share/applications you might have to chmod it first to get access but once there look at one of the .desktop files as a reference i choose xchat.desktop  you will get the general idea of how it works. ass the exec=<programnamehere> and then gave it a category and thats it.[/QUOTE]
 menu editing in gnome is, to put it politely, a joke compared to KDE... it desparately needs a gui application to make it simple to do.

---

### Post by rjr1049 on 2005-02-21
Open a command prompt and type nautilus applications:/// which will bring up a window that you can use to add items to menus.  It is a dreadful system and in need of overhaul as was pointed out but this will work.

Bob

---

### Post by Darrena on 2005-02-21
[QUOTE=rjr1049]Open a command prompt and type nautilus applications:/// which will bring up a window that you can use to add items to menus.  It is a dreadful system and in need of overhaul as was pointed out but this will work.

Bob[/QUOTE]

I don't think this works with Gnome 2.10 which will be shipping with Hoary and that is what the original poster is talking about.

---

### Post by paul cooke on 2005-02-21
[QUOTE=rjr1049]Open a command prompt and type nautilus applications:/// which will bring up a window that you can use to add items to menus.  It is a dreadful system and in need of overhaul as was pointed out but this will work.

Bob[/QUOTE]

this is the message you currently get with Hoary when you try that "trick":

Can't display location

"applications:///" is not a valid location.

Please check the spelling and try again.

---

### Post by delltony on 2005-02-21
[QUOTE=paul cooke]this is the message you currently get with Hoary when you try that "trick":

Can't display location

"applications:///" is not a valid location.

Please check the spelling and try again.[/QUOTE]

Yes according to the standards that is not part of the new gnome and I believe Sabastian has put it on upstream on bugzilla so its possible it might be added into the future arrays.

---

