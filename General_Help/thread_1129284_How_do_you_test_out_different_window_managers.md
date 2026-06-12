---
title: "How do you test out different window managers?"
date: 2009-04-18
forum: General Help
---

### Post by scott8035 on 2009-04-18
Hi, I'm new to Ubuntu (but I've used Redhat and Gentoo from 1998-2003, so I'm not completely lost). I'd like to try out several window managers, and I found the wmanager package that allows me to switch between them. My problem is that when I log in after enabling wmanager, I just get a black screen with a cursor.

I think I followed the directions correctly; I used wmanagerrc-update to create my rc file, and I added "exec wmanager-loop -geometry +570+585" to my .xsession file like it says in "man wmanager-loop".

Am I doing something wrong? Is there a better way to switch between window managers than wmanager?

---

### Post by justin_guerin on 2009-04-18
I'd just install GDM and the window managers you want to test, then select the specific window manager at the GDM login prompt.

The default packages of window maker, black box, after step, etc. should all set themselves up so that you can select them via GDM.

---

