---
title: "root password"
date: 2005-12-08
forum: General Help
---

### Post by sbhuni on 2005-12-08
i just installed ubuntu(not an expert installation) on my system,it didnt ask for a root password,now when i try to login as root,it asks for a root password,so please tell me the default root password.Please help me as i can't shut the system down properly.

---

### Post by 23meg on 2005-12-08
The root account is disabled by default. You're supposed to use sudo for administrative purposes. Please do a search before asking questions, because this has been asked and answered hundreds of times.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by frodon on 2005-12-08
The default root (sudo commands) password should be your user password.

---

### Post by jrib on 2005-12-08
Ubuntu does not use root.  Instead, you use sudo to do administrative tasks.  The first search result for the text search "root password" on the wiki might be helpful to read: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=root+password&fullsearch=Text](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=root+password&fullsearch=Text)

---

### Post by mherring on 2005-12-08
[QUOTE=_jason]Ubuntu does not use root.  Instead, you use sudo to do administrative tasks.  The first search result for the text search "root password" on the wiki might be helpful to read: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=root+password&fullsearch=Text](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=root+password&fullsearch=Text)[/QUOTE]

Well, Ubuntu does not use root only if that is how you want it......You can change it.
As they said, search---the (easy) procedure is out there.
If you're into trivia, Ubuntu is the only distro I've seen that comes this way.

---

### Post by unisol on 2005-12-08
root is disabled in ubuntu by default use sudo instead

---

### Post by julein on 2005-12-08
Well, I have quite strange trouble using some administration features in Gnome. When I log like user and I want to run some administartion app, f.e. synapric, I'm prompted for admin password. I enter valid password, system replys that password is wrong (I didn't misstyped the password or even used any special chars). After a few attempts, the systems stops to reply and when I try to run such an application, nothing happens.

I can run these apps when I log in as a root or from console emulator... It seems to be some strange trouble with PAM (with sudo or gksudo), but I was not able to solve it... Somebody has an idea? Thank you a lot!

---

### Post by 23meg on 2005-12-08
[QUOTE=julein]Well, I have quite strange trouble using some administration features in Gnome. When I log like user and I want to run some administartion app, f.e. synapric, I'm prompted for admin password. I enter valid password, system replys that password is wrong (I didn't misstyped the password or even used any special chars). After a few attempts, the systems stops to reply and when I try to run such an application, nothing happens.

I can run these apps when I log in as a root or from console emulator... It seems to be some strange trouble with PAM (with sudo or gksudo), but I was not able to solve it... Somebody has an idea? Thank you a lot![/QUOTE]
See if the hostname in your /etc/hostname file matches the one in /etc/hosts. Actually it's best if you post your /etc/hosts file here if you're having trouble with command line sudo as well.

---

### Post by julein on 2005-12-09
[QUOTE=23meg]See if the hostname in your /etc/hostname file matches the one in /etc/hosts. Actually it's best if you post your /etc/hosts file here if you're having trouble with command line sudo as well.[/QUOTE]


well, the hostname in /etc/hosts is the same as in /etc/hostname... But I do not experience problems using command line sudo. I have problems, when I log as ordinary user into X and try to run f.e. users-admin (not from console, but from gnome menu), then I am propted for root pswd, I enter correct one, but autentification fails. After few attemts there is even no prompt for password anymore. I was said, that the autentification mechanism is connected with sudo or gksudo, that is why I mentined it... 

Recently I installed Ubuntu to another machine and I have the same problem, so maybe there is some module missing... Anyone has an idea?

---

