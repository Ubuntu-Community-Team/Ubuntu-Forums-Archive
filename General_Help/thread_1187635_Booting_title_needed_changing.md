---
title: "Booting title needed changing"
date: 2009-06-14
forum: General Help
---

### Post by Ceedub2 on 2009-06-14
I installed and tried out the Kubuntu desktop the other day and decided I liked Gnome better than KDE or Kubuntu. 

Somehow I see the the Kubuntu booting up screen with a blue progress bar now. I thought I made Gnome permanent but apparently not. I used to see the KDE login screen too but fixed it by running the reconfigure GDM command in the terminal. 

I would like to get back the Ubuntu boot screen and Ubuntu progress bar. Can anyone help me get it right again. Thanks!

I am running ver 9.04

---

### Post by fooman on 2009-06-14
an easy way is to use startup manager....you can install it with synaptic (system > administration > synaptic package manager),  or just open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install startupmanager
```

after it installs,  open it in system > administration > startup manager

when it opens,  click the appearance tab.  then look in the bottom of that window for "usplash themes" and choose "usplash-theme-ubuntu" from the list.  close startup manager and you should be set.

hope that helps.

---

### Post by Ceedub2 on 2009-06-14
> **fooman said:**
> an easy way is to use startup manager....you can install it with synaptic (system > administration > synaptic package manager),  or just open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install startupmanager
```after it installs,  open it in system > administration > startup manager

when it opens,  click the appearance tab.  then look in the bottom of that window for "usplash themes" and choose "usplash-theme-ubuntu" from the list.  close startup manager and you should be set.

hope that helps.

This helped alot thank you! It now looks like Ubuntu all around. Thanks again

---

