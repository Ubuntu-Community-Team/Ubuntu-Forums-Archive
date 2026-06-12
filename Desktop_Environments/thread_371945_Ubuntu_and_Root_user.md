---
title: "Ubuntu and Root user"
date: 2007-02-27
forum: Desktop Environments
---

### Post by greywolf79 on 2007-02-27
I know I can use sudo and su commands on the terminals to get root access to files but there are still some files it says I cannot edit or alter. When I try to log in as root it basicly says root account cannot be accessed through the gui... Any idea what I should do to log in as root? or even how to log in as root? As the only user on the system I should already have root privaledges anyway right? The last time I looked at users on the system there was a root user disabled but even after I enabled root it still gave me same problem with logging in as root... Any ideas?

---

### Post by tsg1zzn on 2007-02-27
If you are root but cannot edit files it means their permission is set like that. However, since you're root, you can still change the permissions. Then you can edit the files.

To enable login as root, type sudo passwd to set a root password. Then you can login as root.

---

### Post by greywolf79 on 2007-02-27
Ah... I never thought about changing the permissions. Thank you. I will try that next time I need to access a file. Thank you for your help.

---

### Post by eggdeng on 2007-02-27
Another neat trick is to type ```
sudo nautilus
``` in a terminal, which gives you superuser privileges in gui mode.

---

### Post by mcduck on 2007-02-27
> **tsg1zzn said:**
> If you are root but cannot edit files it means their permission is set like that. However, since you're root, you can still change the permissions. Then you can edit the files.

To enable login as root, type sudo passwd to set a root password. Then you can login as root.

This is very easy way to break your system. Many system files need to have certain permissions, and changing them might lead into unusable system. Don't do it.

Also logging into desktop as root is not very wise thing to do, you would be running all applications with root privileges.

The best way is to use 'sudo' for terminal apps and 'gksudo for graphical ones. For example use 'gksudo gedit filename' to open a file for editing as root, and if you need, 'gksudo nautilus' to open a file manager as root. From there you can do pretty much anything (just be careful with it, it allows you to break your system if you do any mistakes like remove wrong files..)

---

### Post by 23meg on 2007-02-27
> **eggdeng said:**
> Another neat trick is to type ```
sudo nautilus
``` in a terminal, which gives you superuser privileges in gui mode.

Since Nautilus is a graphical app, you should use *gksudo* instead of *sudo* with it.

```
gksudo nautilus
```

---

### Post by benphane on 2007-02-27
So, for me, getting into the groove of "sudo this" and "gksudo that" will be no big deal.  

Has anyone put thoughts to screen on making basic admin/configuration tasks a little more "transparant" for the Microsoft convert?

---

### Post by oldsparks on 2007-02-28
> ** said:**
> 
If you really do need to log in as root (rather than using sudo) key
Ctl+Alt+F1  after a few seconds of blackness you will be asked to login. Login as root (make sure you know the password for root first).
When you have finished working as root, key
Ctl+Alt+F7 and you will go back to the GUI with your original login.
It is easy to bugger up your system when working as root - so do not do anything you are not sure about.

---

### Post by aysiu on 2007-02-28
> **benphane said:**
> So, for me, getting into the groove of "sudo this" and "gksudo that" will be no big deal.  

Has anyone put thoughts to screen on making basic admin/configuration tasks a little more "transparant" for the Microsoft convert? Yes. Knoppix and Mepis did. Unfortunately, Ubuntu still has not. So you need to create a launcher or keyboard shortcut for the appropriate command: ```
gksudo nautilus
``` ```
kdesu konqueror
``` ```
gksudo thunar
```

---

### Post by sgstarling on 2007-02-28
> **mcduck said:**
> 
The best way is to use 'sudo' for terminal apps and 'gksudo for graphical ones. For example use 'gksudo gedit filename' to open a file for editing as root, and if you need, 'gksudo nautilus' to open a file manager as root. From there you can do pretty much anything (just be careful with it, it allows you to break your system if you do any mistakes like remove wrong files..)


I find it conveinent to make launcher for ROOT file manager, with that start command: "gksudo nautilus".  I use a special Red icon as an additional reminder that I'm about to mess with fire...

---

