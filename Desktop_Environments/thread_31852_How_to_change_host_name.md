---
title: "How to change host name"
date: 2005-05-05
forum: Desktop Environments
---

### Post by juvito cham on 2005-05-05
Helo my friend ,please tell me how to change my host name ?
thank for your colaboration

---

### Post by nad on 2005-05-05
sudo gedit /etc/hostname

---

### Post by calvinpriest on 2005-05-05
You can also do it through the GUI via System->Administration->Networking and then going to the General tab.

---

### Post by tjb4u on 2006-07-19
If you choose not to do change the host name through the GUI or do not have the GUI available (e.g. server install) make sure to change occurences of your old hostname to the new hostname in both **/etc/hostname** and **/etc/hosts** or else you'll mess up your ability to use sudo.

---

