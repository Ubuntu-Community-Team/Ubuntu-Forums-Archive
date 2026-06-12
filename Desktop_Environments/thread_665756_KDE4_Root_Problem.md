---
title: "KDE4 Root Problem"
date: 2008-01-12
forum: Desktop Environments
---

### Post by JustinAlf on 2008-01-12
I did a search and came back with nothing.  Does anyone know why my root password doesn't work with KDE4?  I can't get Synaptic or Adept to work.

---

### Post by kellemes on 2008-01-12
> **JustinAlf said:**
> I did a search and came back with nothing.  Does anyone know why my root password doesn't work with KDE4?  I can't get Synaptic or Adept to work.

You have a root-password on Ubuntu?
You mean your own password for getting root-access?

---

### Post by p_quarles on 2008-01-12
Based on what I've seen, Adept in KDE4 (the final release -- not the one in the repositories) is set up to authenticate with root's password, rather than the sudoers password. 

I'm not sure this will do anything, but give it a shot: run Adept manually as the user:
```
kdesu adept-manager &
```

---

### Post by cheelay on 2008-01-12
I think the easiest fix is to go to the konsole and type "sudo passwd" and then retype your normal user password. Once that gets setup again all should be well.

Worked for me.

---

### Post by kellemes on 2008-01-13
> **p_quarles said:**
> Based on what I've seen, Adept in KDE4 (the final release -- not the one in the repositories) is set up to authenticate with root's password, rather than the sudoers password.

For this you need a root-account.. Can't imagine *buntu using a root-account for this.
Could be wrong though..

---

### Post by JustinAlf on 2008-01-14
Well, this seems to be an odd problem.  If I go into Konsole and type sudo -s and then go into adept, it works fine.  But if I select adept form the K-Menu, it asks for a root password.  I type in the root password and it says that it's incorrect.

---

### Post by kellemes on 2008-01-16
> **JustinAlf said:**
> Well, this seems to be an odd problem.  If I go into Konsole and type sudo -s and then go into adept, it works fine.  But if I select adept form the K-Menu, it asks for a root password.  I type in the root password and it says that it's incorrect.

What's the command used in the menu-entry?

---

