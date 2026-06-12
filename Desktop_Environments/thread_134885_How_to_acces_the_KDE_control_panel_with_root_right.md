---
title: "How to acces the KDE control panel with root rights"
date: 2006-02-22
forum: Desktop Environments
---

### Post by SivArt on 2006-02-22
I have set up a workstation with kubuntu linux and I want to add an additional user, what I want to know is the root pasword or how to login as root (remove sudo).

Thank you!!!

---

### Post by SivArt on 2006-02-22
I was trying to enable the root account or to create a new account but each time I do that Kuser crashes
does anybody knows how to disable sudo, so I can log using the root or is any workaround for the Kuser issue.


Thank you!!

---

### Post by Jucato on 2006-02-22
What version of KDE are you using? most of the Administrator Mode bugs using KControl modules have been fixed in KDE 3.5.1

Alternatively, have you tried using sudo kuser (from the command line) or kdesu kuser (from a Run dialog box).

When sudo asks for the password, it is asking for your password. maybe this link could help: [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by SivArt on 2006-02-22
I am using **Kubuntu Breezy 5.10** and I never experience this problem before, I don't know what is happening but is crashing. Do you know about any specific bug/patch?

thks

---

### Post by Jucato on 2006-02-22
Kubuntu is different from KDE. Kubuntu is a Linux *distrobution* that uses the KDE *desktop environment*. The Kubuntu installer installs KDE version 3.4.x, while the latest is KDE 3.5.1.

But before you go upgrading, you should try out a few tests first. Have you tried running kuser from the command line (sudo kuser)? Is this crash only happening to kuser or to some things that need administrator mode as well?

---

### Post by SivArt on 2006-02-23
I know that Kubuntu is diff from KDE, KDE as Gnome are Window managers (The GUI). I already tried to apply the kuser command on console but it crashes when I tried to create modify or delete an user/group.

I do not know the cause of this but I want to now if someone has experience something similar to this with kuser and how to solve it.

Thanks for your replies Fenix:).

Note: The crash only happens with kuser.

---

