---
title: "Setting default session type"
date: 2012-08-21
forum: Desktop Environments
---

### Post by caustin76 on 2012-08-21
Some background.  I am working on a Linux solution for my enterprise environment.  Ubuntu looks to be the best choice for us so far.  I have my image authenticating against my AD controllers.  My next issue is this.  I installed KDE 4.9 and want to use this as a default desktop for all users(current and future) to make it easier for my users to transition.  I've determined that I need to edit the lightdm.conf file.  what do i set the 'user-session' to?  I've tried KDE and kubuntu, but it drops me back at the login screen. Thanks.

---

### Post by spjackson on 2012-08-21
I'm not an expert with this, but I think you need to install the kubuntu-desktop package, not just KDE, then set user-session=Kubuntu. In any event, the session you specify needs to match a .desktop file in /usr/share/xsessions/

[See here]("http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins") for more information.

---

