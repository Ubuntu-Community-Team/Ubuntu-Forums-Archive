---
title: "firefox looks ugly: gtk2-engines-gtk-qt problem"
date: 2006-01-16
forum: Desktop Environments
---

### Post by bennettg on 2006-01-16
hi. nOOb here.  need help/

I just did a fresh install of kubuntu 5.10.  used arnieboy's amazing automatix script to install firefox with plugins, etc.

previously to this fresh install, my last kubuntu 5.10 i was able to go into the system settings, appearance, gtk styles and fonts, and under gtk styles choose another style and font and gtk2-engines-gtk-qt was there.  

with this, i do not see it from the drop down menu, only raleigh.  I verified in adept that gtk2-engines-gtk-qt is installed. 

why won't this work?/??  please help me

---

### Post by obibok on 2006-01-17
I guess you got no replies because you did everything correctly :confused:

What version of KDE are you running: stock 3.4.3 or upgraded to 3.5? Have you tried installing any other gtk2-engines-* just for testing?

Check if you have:
/usr/share/themes/Qt/gtk-2.0/gtkrc
/usr/lib/gtk-2.0/2.4.0/engines/libqtengine.so
/usr/lib/kde3/kcm_kcmgtk.so

Reconfigure/reinstall gtk-2-engines-gtk-qt maybe...?

---

### Post by lamego on 2006-01-17
My fonts also turned a mess after using Automix,  it was related to the mtt fonts which I have choosen to install.
Removing the MS TT fonts resolved the problem fo rme.

---

### Post by Zotova on 2006-01-17
How exactly does Firefox look ugly? Could you post a screenshot or something.

You could try installing the Plastikfox theme for Firefox - that gives it a more KDE feel. I find your problem interesting however as I have gtk2-engines-gtk-qt and it makes everything look KDE'ish except synaptic - that still looks ugly and Windows 95ish under KDE.

I'm using 3.5 btw.

---

### Post by GoldBuggie on 2006-01-17
To fix so that synaptic work as well do
```
sudo ln -s ~/.qt/qt_plugins_3.3rc /root/.qt/qt_plugins_3.3rc
sudo ln -s ~/.qt/qtrc /root/.qt/qtrc
```

---

### Post by Navyblue on 2006-01-18
Not sure of this is your case.

I find that a freshly installed Kubuntu, GTK applications only made use of QT colours but not QT widgets (despite it says so in the GUI). To do that, I need to go to the System Settings - Appearance - GTK Styles & Fonts, Select other styles, select back KDE styles and click apply. You might need to restart X (I'm not sure). Also if you are running a newly installed GTK application for the first time it would still use GTK widget, subsequent run are fine.

---

