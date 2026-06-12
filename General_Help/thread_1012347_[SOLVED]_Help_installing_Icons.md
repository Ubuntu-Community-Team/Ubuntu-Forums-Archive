---
title: "[SOLVED] Help installing Icons"
date: 2008-12-15
forum: General Help
---

### Post by securitynut on 2008-12-15
Hi all. I'm new to Ubuntu and have found my away around pretty quickly. I'm trying to install icons but when i try to install them it says the installation failed. I'm going to System->Preferences->Appearance and clicking install theme. Any help would be great. Thanks.

---

### Post by Wartender on 2008-12-15
ok you can also do this, go to your home, and click ctrl+h to show hidden files, then extract the folder of your icon theme into that directory (that is to say, you want the actual folder there, not the compressed file), now when you go to appearance and click customize it should be in the list of icon themes.

---

### Post by securitynut on 2008-12-15
I put the folder there but it's still not showing up where you select the icons.

---

### Post by Wartender on 2008-12-15
WHOOPS! my bad, you have to go into the .icons folder after showing hidden folders and paste it THERE... wow can't believe i forgot to put that! retard moment :P

---

### Post by securitynut on 2008-12-15
I moved it to the .icons folder but still didn't show. Any suggestions? It's the hydroxygen iconset.

---

### Post by Wartender on 2008-12-15
huh. weird. not sure what to do then... try downloading it again?

---

### Post by Ivo Moelans on 2008-12-15
Could you give the name of the theme, the extension of the file and where you downloaded it?

---

### Post by securitynut on 2008-12-15
Its called hydroxygen iconset, when downloaded it comes as a zip file with 2 text documents inside, a jpg inside for customizing and a .bz2 tarball. I downloaded it from [www.gnome-look.org](www.gnome-look.org). It's weird because I got these icons working on my laptop, though i can't remember what i did.

---

### Post by Wartender on 2008-12-15
how strange, i downloaded it from there as well, and it works fin eon both my desktop and my mother's laptop. not sure man.

---

### Post by Ivo Moelans on 2008-12-15
Yep, the same here. Though I downloaded via the direct link and my file came as a tar.bz2.

---

### Post by Ivo Moelans on 2008-12-15
Just to make sure: when you unpack *hydroxygen_iconset.tar.bz2* you should get a directory called *hydroxygen*. When you move that directory manually to */home/<username>/.icons* it still doesn't show up?

---

### Post by louistan3 on 2008-12-15
i put mine into /usr/share/icons

i think its much better because even sudo applications can use them.

but then again, im not sure if thats safe or what not.

as regarding to the icon set, if i remember right, can't you just drag and drop onto the appearance window?

sorry im not much help

---

### Post by securitynut on 2008-12-15
It works now. Copied the folder to /usr/share/icons. Thanks for the help everyone.

---

