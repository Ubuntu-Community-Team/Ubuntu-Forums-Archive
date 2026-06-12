---
title: "[SOLVED] Themes problem"
date: 2008-02-26
forum: Desktop Environments
---

### Post by linux phreak on 2008-02-26
Hi,im using xubuntu 7.10 and today i went to xfce-look.org and downloaded some themes.I installed it by placing them inside the .themes folder.Now i find that synaptic package manager and update manager are not skinned but the rest of the applications are.Can i solve this.

---

### Post by geekcliff on 2008-02-27
Thats normal, ive seen this too, not sure why it does it, i think its to do with the way these apps are written. :lolflag:

---

### Post by linux phreak on 2008-02-27
Does it happen with ubuntu/kubuntu too?

---

### Post by geekcliff on 2008-02-27
Ive not seen it in the others, unless you mix and match gnome with KDE, i think  the two items you mention are actually gnome apps thats why they look different with certain themes, i usually just ignore it, but i dont expect thats much help to you.

---

### Post by misfitpierce on 2008-02-27
Simple.... go into theme manager as sudo to change

w/e appearance name is

Ex: sudo gnome-appearance-properties - just example... then all super user apps will be skinned w/e you set inside it.

---

### Post by jayde6 on 2008-02-27
It is because the .themes folder in your home directory is for your user name. Syanptic runs as root, so you would have to copy the themes to /usr/share/themes. You will need to be root to copy them to the folder however.

```
sudo cp /home/<usr-name>/.themes/<theme-name> /usr/share/themes
```

---

### Post by linux phreak on 2008-02-27
Thanks jayde6.That worked

---

### Post by geekcliff on 2008-02-27
Well, thats helped me as well, thank you for that.:popcorn:

---

