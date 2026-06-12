---
title: "Ubuntu 16.04 LTS - How to restore icons"
date: 2017-02-15
forum: Desktop Environments
---

### Post by ubu112 on 2017-02-15
Please,after a problem with Classic Menu Indicator,that I removed,I lost many icons,some changed colour,some aren't the same.I tried with Unity Tweak Tool and others,but nothing changed.Can someone help me.Thank you

---

### Post by Frogs Hair on 2017-02-17
Hello and Welcome !

What icon set/s was affected ?

---

### Post by ubu112 on 2017-02-17
Thank you "Frogs Hair" for your answer.Was affected System Settings,lost 50% icons,and the top bar icons changed.But now with the help of Ubuntu Tweak and luck,because I'm a beginner,I fixed it. The last problem is on the desktop, one icon is changed and I'm not able to change it.At the end I tried to install again Classic Menu Indicator,that was the beginning of my problems and it's working.Have you suggestions to give me to restore the last icon on the desktop?Thank you

---

### Post by Frogs Hair on 2017-02-18
Is this icon included with the desktop icon settings in Ubuntu Tweak or an application icon you added to the desktop ?

---

### Post by ubu112 on 2017-02-19
One is a shortcut to a web page,it works,but changed icon and one,very strange,a folder with the same name of the shortcut,but all changed inside but I don't remember what it was,so I removed it.Added from me.I notice that inside Home I have many more folder (.adobe,.cache,.compiz,.config,.dbus,.gconf,etc)what can I do with these folders?Thank you

---

### Post by Perfect Storm on 2017-02-19
Those files are your user configurations files and user preferences. Don't delete them it will reset your user settings. Apparently you have set your file browser to see hidden files. Hidden files are marked with a dot infront. You can hide those files again if you check the tabs in the filebrowser that a ticked 'show hidden files'.

---

### Post by aparunpandian on 2017-02-19
open terminal and Type following command: 
gsettings set org.gnome.desktop.interface icon-theme ''

---

### Post by ubu112 on 2017-02-20
"Artificial Intelligence"I'd like to say Thank you.All files with dot infront,now are hidden.Thank you very much

---

