---
title: "adding new theme to cairo dock"
date: 2009-03-22
forum: Desktop Environments
---

### Post by firewarrior on 2009-03-22
I just got cairo dock for my desktop. I have downloaded a couple of new themes that i want to add to it but can not figure out how. Can anyone out there help me figure this out? Thanks ahead of time.

---

### Post by fabounet on 2009-03-23
uncompress them and copy them to ~/.config/cairo-dock/themes

---

### Post by firewarrior on 2009-03-23
I have tried dragging and drop. I've tried opening all in the terminal. Everytime I try putting these files in the themes folder all I get is an error message saying that permission is denied. I can't figure out what is going on here.

---

### Post by Celosodia on 2009-03-23
I'm not sure about yours, but my Cairo-dock folder is in my file system. To be able to paste something into your file system, you need to login as super user. Open a terminal and type in "su" without the quotation marks. It should then ask for your password. After that is done, you should have the authority to put your themes into the folder.

---

### Post by fabounet on 2009-03-24
that's very abnormal, how did you install it ?
the conf files should be in ~/.config/cairo-dock, or you should reinstall it.

---

### Post by YAHisKING777 on 2013-01-22
> **firewarrior said:**
> I have tried dragging and drop. I've tried opening all in the terminal. Everytime I try putting these files in the themes folder all I get is an error message saying that permission is denied. I can't figure out what is going on here.

Theme folders need root permissions in order to write to them. Simply right click on the folder, and click "open as root". Then you will be given elevated privileges, so you could add themes to the folder.

---

