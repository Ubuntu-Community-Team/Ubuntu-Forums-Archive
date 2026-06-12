---
title: "Need to get rid of &quot;Desktop&quot; and Xfce Panel&quot; from pypanel"
date: 2008-03-17
forum: Desktop Environments
---

### Post by Alucard-sama on 2008-03-17
I'm currently using Xfce with the Openbox WM as my primary desktop and I decided to use pypanel as a replacement for one of my Xfce panels, the only problem is in the pypanel there is a entry saying "Desktop" and another saying "Xfce Panel" how do I get rid of these?
Pleas help they take up quite a lot of space on the panel.

---

### Post by Alucard-sama on 2008-03-17
Okay I think I have it figured out, I just have to list the applications in /etc/pypanelrc in the hide list like so:
> HIDE_LIST       = ["xfdesktop", "xfce4-panel"]  
This hasen't worked though :\

---

### Post by Alucard-sama on 2008-03-17
Alrighty I figured it out, needed to put the information into ~/.pypanelrc.

---

