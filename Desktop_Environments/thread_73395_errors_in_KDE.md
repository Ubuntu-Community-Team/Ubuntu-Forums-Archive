---
title: "errors in KDE?"
date: 2005-10-08
forum: Desktop Environments
---

### Post by rhys_rhaven on 2005-10-08
I recently installed Kubuntu, and when i try to go into the user control panel, (to change the user password) clicking on administrator mode  brings up a screen that says loading, where it stays indefinatly. this happens on any window in the control panel with "administrator mode." 

i did use -sudo passwd root- to set a root password, that there wasnt one rather bugged me. could someone clarify what the purpose of this was? can everything be done with a user password? any help would be much appreciated. 

"and why i just had to edit this 6 times is beyond me, excuse any errors my caffinee lacking mind has missed."

---

### Post by aysiu on 2005-10-08
[QUOTE=rhys_rhaven]I recently installed Kubuntu, and when i try to go into the user control panel, (to change the user password) clicking on administrator mode  brings up a screen that says loading, where it stays indefinatly. this happens on any window in the control panel with "administrator mode."[/quote] I don't know what's going on here, but you can also manually edit the config file by typing ```
sudo nano /etc/kde3/kdm/kdmrc
```

> 
i did use -sudo passwd root- to set a root password, that there wasnt one rather bugged me. could someone clarify what the purpose of this was? can everything be done with a user password? any help would be much appreciated.  Read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by rainbow_fire on 2005-10-09
I had that prob;lem once too then i used the the little icon that says Kuser it atomaticly takes you into root mode and alows your passwords to operate normaly It is somthing about how Kde operates i think i am newbie too :o)

---

### Post by rhys_rhaven on 2005-10-09
thanks alot. just for anyone else who has this problem.

Enabling the root account

Note: This is not recommended! It will break all the GUI admin tools < as in, broke the KDE control panel. 

run this 
sudo passwd -l root
This locks the root account. < and fixes the problem. (problem being the user was an idiot. :-\)

---

