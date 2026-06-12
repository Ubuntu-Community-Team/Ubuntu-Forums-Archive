---
title: "How to create same desktop settings for new users?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by ttry72 on 2006-09-19
After a few months my family are more intresting in the Ubuntu. Perhaps one reason is my cool candy-eye desktop which looks like improved Mac OS X :D 

So, now I am in the situation where I need to create new user accounts. The creation is not the problem but the problem is that how can I generate the same settings of my desktop for them? I am sure there are a way how to create/edit default layout of the desktop.

My version is 6.06 and it uses the Gnome.

Thanks in advance,
Tuomo

---

### Post by skymt on 2006-09-19
When a new user is created, their home directory is created from a template at /etc/skel (skel is for skeleton). Copy any config files you want new users to have to this directory.

EDIT: For GConf, try [Sabayon](http://www.gnome.org/projects/sabayon/).

---

### Post by ttry72 on 2006-09-20
Thank you very much, I'll try to find out this.

---

