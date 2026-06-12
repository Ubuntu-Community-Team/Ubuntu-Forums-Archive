---
title: "Restricted-user updates in KDE 4?"
date: 2009-09-09
forum: Desktop Environments
---

### Post by russell-ault on 2009-09-09
This may seem like an odd question, but I think the answer will be useful to anyone who manages computers with used by non-technical users.

The situation:
My sister has a computer but doesn't feel comfortable doing administrative tasks beyond simple updates.

The solution in KDE 3.5:
Add my sister to a group that has sudo access to apt-get and whatever graphical program(s) KDE uses to install and update software.

The problem in KDE 4:
KDE 4 (at least the version used in jaunty) handles updates through a kcmshell module. My sister literally doesn't want the amount of power one gets from sudo access to every kcmshell module (yes, I've asked her) and I can't seem to find a way to tell sudo to let her run the kcmshell command as root only if it's run with certain options (i.e. only if it's run to do a system update).

The work-around/kludge:
A hastily-composed shell script with a link on her desktop that runs 'sudo apt-get update && sudo apt-get upgrade' that I've told her to run when she sees there is an update.

Obviously this is an inelegant solution, especially since it is relatively un-obvious to the lay-user and so requires some user reeducation. Ideally the user would be able to double-click on the system tray update icon, enter his/her password, and the system would update, without having to allow the user the ability to do anything beyond that. Does anyone know how to do this given the current framework?

---

