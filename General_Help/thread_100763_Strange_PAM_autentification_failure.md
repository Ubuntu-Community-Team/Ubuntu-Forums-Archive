---
title: "Strange PAM autentification failure"
date: 2005-12-08
forum: General Help
---

### Post by julein on 2005-12-08
Well, I have quite strange trouble using some administration features in Gnome. When I log like user and I want to run some administartion app, f.e. synapric, I'm prompted for admin password. I enter valid password, system replys that password is wrong (I didn't misstyped the password or even used any special chars). After a few attempts, the systems stops to reply and when I try to run such an application, nothing happens.

I can run these apps when I log in as a root or from console emulator... It seems to be some strange problem with PAM (with sudo or gksudo), but I was not able to solve it... Somebody has an idea? Thank you a lot!

---

### Post by eitan on 2005-12-08
i wonder..
  if you invoke the
     System -> Lock Screen
  command, do you have the same problem?
  (i.e. cannot log back in even though you enter the correct
   password?)

  i have the problem you describe, but with the lock screen feature,
  not with the gksu password prompts for synaptics or other 
  apps that require admin privileges.

---

### Post by julein on 2005-12-09
Actually no. when I lock the screen, I enter my user password (I do not need to use root password for that) and everytings ok, the problem appears only when trying to run any app which needs root privilegies ...

---

### Post by dtessier on 2005-12-09
[QUOTE=julein]I'm prompted for admin password.[/QUOTE][QUOTE=julein]It seems to be some strange problem with PAM (with sudo or gksudo)[/QUOTE]

When you use sudo/gksudo, you're prompted for your own password, not the root password.

---

### Post by julein on 2005-12-09
[QUOTE=dtessier]When you use sudo/gksudo, you're prompted for your own password, not the root password.[/QUOTE]

Well, I do not have problems, while using sudo from console, but when I am logges as ordinary user and try to run f.e. users-admin (not from console, but from menu), then I am prompted for root password. I enter correct password but autentification fails. But I wa said, that this mechanism is connected with gksudo...

---

