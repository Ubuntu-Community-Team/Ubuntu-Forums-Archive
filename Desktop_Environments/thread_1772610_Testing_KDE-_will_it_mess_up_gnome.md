---
title: "Testing KDE- will it mess up gnome"
date: 2011-05-31
forum: Desktop Environments
---

### Post by Purplerob on 2011-05-31
I want to try KDE, I think I might like it. But I don't want it if it will interfere with gnome and unity. So, if I install the kubuntu-desktop package will it affect my computer. Also, if I don't like it how can I remove kde %100 with nothing remaining?

---

### Post by dFlyer on 2011-05-31
I have not used KDE for many years. But back in the 90's when I tried it, most distros installed both kde and gnome in a standard install. I don't see how it can hurt gnome. As far as removing it, someone else will have to help you there.

---

### Post by Purplerob on 2011-05-31
Thanks, 
does anyone know about removal?

---

### Post by blauendonau on 2011-05-31
> **Purplerob said:**
> Thanks, 
does anyone know about removal?

If you follow the instructions at this link you should be able to remove Kubuntu (or most of the other DEs) and return to a clean GNOME/Unity without problems.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

In my experience, there may be slight inconsistencies in GNOME when you run other DEs alongside it but they don't affect performance and can usually be corrected easily. Do be prepared to have your menus cluttered up a bit because you will have both KDE and GNOME applications installed.

---

### Post by Purplerob on 2011-05-31
Thanks! I'm installing KDE right now!

---

### Post by Purplerob on 2011-05-31
new problem: the option to log in on gdm for kde/kubuntu is missing. Does anyone have the kubuntu login file for the /usr/share/xsessions directory.

---

### Post by hhh on 2011-05-31
Use one of the existing .desktop files as a template by opening it in a text editor and saving it as kde.desktop . Then change the "Name" field to "KDE Session" (without quotes) and the Exec field to startkde .

---

