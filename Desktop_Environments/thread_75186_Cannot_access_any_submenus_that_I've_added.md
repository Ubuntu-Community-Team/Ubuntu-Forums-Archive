---
title: "Cannot access any submenus that I've added"
date: 2005-10-13
forum: Desktop Environments
---

### Post by ezHiker on 2005-10-13
Hello.

I've attempted to add some submenus to my applications menu, and the problem is that I can't see them. If I go into the menu editor I can see them, but they are disabled, and I can't click the check box to enable them.

Anyone have any idea what would cause this?  I have another machine running Breezy with the same updates and everything, but it doesn't have this problem.

Thanks.

---

### Post by kassetra on 2005-10-13
[QUOTE=ezHiker]Hello.

I've attempted to add some submenus to my applications menu, and the problem is that I can't see them. If I go into the menu editor I can see them, but they are disabled, and I can't click the check box to enable them.

Anyone have any idea what would cause this?  I have another machine running Breezy with the same updates and everything, but it doesn't have this problem.

Thanks.[/QUOTE]

One of the problems may be permissions - make sure that you own everything inside of your home directory.... two quick commands on the terminal will make everything in your home directory owned & writable by you: 

```
sudo chown -R username.username /home/username
sudo chmod -R 755 /home/username
```
You will need to know your username, and your own password (it will ask you for it.)

---

### Post by ezHiker on 2005-10-13
Thanks for the suggestion, but unfortunately after resetting the ownership and permissions, the problem persists. :(

---

### Post by nutshell on 2005-10-13
the 'smeg' tool is very useful for editing the Gnome menu.

---

### Post by CapnCook on 2005-10-13
This has happened to me several times. Just log out and log back in and you should see the menu items them.

---

### Post by ezHiker on 2005-10-13
Just to clarify:

Smeg is what I used to add the submenu.

I've also tried logging off and back on, but no dice...

---

