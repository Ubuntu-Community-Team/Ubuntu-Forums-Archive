---
title: "Saving a file"
date: 2008-12-28
forum: General Help
---

### Post by LightHeart on 2008-12-28
Hello guys, i want to make an edit in the nsswitch.conf file however every time i make a change and try to save i get the error: "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." What does that mean? I am the admin

---

### Post by p_quarles on 2008-12-28
> **LightHeart said:**
> Hello guys, i want to make an edit in the nsswitch.conf file however every time i make a change and try to save i get the error: "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." What does that mean? I am the admin
By default, your session does not operate on the assumption that you have root privileges. You have to tell the computer that you want those. This is pretty easy. From the alt-F2 dialogue, type:
```
gksudo gedit
```
to open the editor. It will ask for your password, then open the text editor. Click "open file" and so forth -- then you will be able to save your changes.

---

### Post by fooman on 2008-12-28
you need to have temporary root priviledges using sudo or in this case *gksudo*,  since it will be using a gui editor...try this in a terminal:

```
gksudo gedit /etc/nsswitch.conf
```

edit: too slow again!

---

### Post by LightHeart on 2008-12-28
Thank you so much!

---

