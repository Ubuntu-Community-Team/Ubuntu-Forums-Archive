---
title: "How do I prevent X from starting at boot up?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by CzarAlex on 2006-09-05
Greetings, 
    I started with a desktop install that kinda turned in to a server mostly. Now, Id like to free up some memory by preventing X (in this case, Gnome) from starting when the system boots up. The command line is just what I want. 

How can I do this? Id rather not uninstall anything, but just tell the system to NOT load Gnome and just give me the command line. Suggestions? Basically, I want to convert a Desktop install to a server install (no more GUI)

---

### Post by meng on 2006-09-05
What I did was the following:
cd /etc/rc2.d
sudo mv S13gdm _S13gdm

The benefit about this method is that it's easy to undo.

---

### Post by CzarAlex on 2006-09-06
Absolutly perfect! I appreciate the reply! :mrgreen:

---

### Post by yota on 2006-09-06
Hi,

a convenient command to manage which service is automatically started is 'update-rc.d'.

Have a look at:
```

man update-rc.d

```

---

