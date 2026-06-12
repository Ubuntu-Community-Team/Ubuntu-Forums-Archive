---
title: "How do I change the K Menu Icon?"
date: 2007-04-06
forum: Desktop Environments
---

### Post by wersdaluv on 2007-04-06
I just installed Kickoff.

It's nice but I don't like the icon. It's an oversized Kubuntu Icon.

How can I change it?

---

### Post by mexlinux on 2007-04-06
The icons of kickoff are located here:
/usr/share/apps/kicker/pics

Back up and replace with your choice

---

### Post by lunamystry on 2007-09-13
I don't know what kickoff is but I would like to change my K-menu icon. I have kicker and when i go to the directory given i don't find the k-menu icon there. How do I change the k-menu icon to one that i found from kde-look?

---

### Post by kuja on 2007-09-13
> **lunamystry said:**
> I don't know what kickoff is but I would like to change my K-menu icon. I have kicker and when i go to the directory given i don't find the k-menu icon there. How do I change the k-menu icon to one that i found from kde-look?

Easiest way would be to replace the /usr/share/icons/default.kde/48x48/apps/kmenu.png file, I would presume.You may need to replace the icon at other sizes as well. Alter the directory to match the theme you're currently using. (kde default is of course Crystal)

---

### Post by lunamystry on 2007-09-13
THANK YOU!! 

I'll see what happens.

---

### Post by lunamystry on 2007-09-13
While browsing through KDE-look I found out that there is an application called kbfx which is a sort of replacement for k menu. I went to konsole and:

[INDENT]sudo apt-get install kbfx[/INDENT]

and I can now change my k menu with a graphical interface. Thought i would just share. :)

---

### Post by Happy_Man on 2007-09-13
That's not really part of KDE, though.

---

### Post by lunamystry on 2007-09-15
That must explain why every time I change something and apply it takes so long to respond.

---

