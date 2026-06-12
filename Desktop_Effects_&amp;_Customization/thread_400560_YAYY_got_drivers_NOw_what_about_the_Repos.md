---
title: "YAYY got drivers??? NOw what about the Repos??"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by CorranSW on 2007-04-03
Hi i just posted an hour ago about  a problem installing the nvidia drivers on ubuntu.... I think i got em now being as my moniter is running at a 1900 resolution... something i couldent acheive before.... and a nvidia logo appears when i start ubuntu... So ummm what about the repos? Does anyone have the terminal code to get the repos??? all the guides i look at seem to have old repos that dont exist any more from wherever they were being downloaded....

---

### Post by CorranSW on 2007-04-03
what command do i use in the terminal to check if i have the drivers installed?

---

### Post by CorranSW on 2007-04-03
specifically the error i get when i try to install the repos through terminal is..
gangster@gangster-desktop:~$ sudo apt-get install beryl emerald-themes
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
gangster@gangster-desktop:~$

---

### Post by sisco311 on 2007-04-03
```
gksu gedit /etc/apt/sources.list
```
copy/paste this on the end of the file
> deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
Ctrl-s, Alt-F4(save the file and exit)
in terminal:
```
sudo apt-get update
```
than try to install beryl

---

