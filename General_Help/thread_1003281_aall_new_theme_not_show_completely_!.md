---
title: "aall new theme not show completely !"
date: 2008-12-05
forum: General Help
---

### Post by anhvu2875 on 2008-12-05
i installed new themes for my Intrepid but in some case theme not show completely such as when i open and run : synaptic , update manager , nautilus -> still the old themes ( default ) !

---

### Post by eternalnewbee on 2008-12-06
Are you running compiz?

---

### Post by binbash on 2008-12-06
you will copy your .theme .fonts and .icons to /root OR link them (prefer linking! )

---

### Post by anhvu2875 on 2008-12-06
**eternalnewbee**
yes
**binbash**
how can i link them ?

---

### Post by binbash on 2008-12-06
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

---

### Post by anhvu2875 on 2008-12-06
**binbash**
oh , i got it , thanks ! and i have to do like that again everytime i change new themes including stock themes ?

---

### Post by binbash on 2008-12-06
> **anhvu2875 said:**
> **binbash**
oh , i got it , thanks ! and i have to do like that again everytime i change new themes including stock themes ?

do it once that is all

---

### Post by eternalnewbee on 2008-12-06
Compiz overrules default gnome themes.
If you have **Compiz Fusion Icon installed**, right-click on it, and under **Select Window Manager** choose **Compiz**, and under **Select Window Decorator** choose **GTK**. That should do it.

---

