---
title: "Can't boot to GNOME desktop, login box says my password is invalid"
date: 2007-01-01
forum: Desktop Environments
---

### Post by itsjustarumour on 2007-01-01
Help! - I selected a different Gnome login theme, rebooted and now I can't log in!  The old login theme is still there, and it just tells me that my username or password is invalid - which it isn't!  ](*,) 

My root password still works - I can open a Failsafe Gnome session OK, open up a terminal and try "startx", which gets me to the login manager again.  I've tried installing KDM as well, then selecting "KDE" from the login manager, but get the same problem.

I've been trying to fix this for 2 days and being faily new to Ubuntu I'm completely lost...  How do I solve this?  Is there a way to log on as root, and change my user-id password from the terminal?  Or is there a process running somewhere thats locked me out, that I can kill somewhere?  Any help or wisdom very gratefully received!! :D 

(Edgy 6.10 32bit Gnome 2.16)

---

### Post by adaptr on 2007-01-01
> **itsjustarumour said:**
> Help! - I selected a different Gnome login theme, rebooted and now I can't log in!  The old login theme is still there, and it just tells me that my username or password is invalid - which it isn't!  ](*,) 
Are you absolutely, positively certain ?
This is not a joke, either one is invalidated by a single typo.
Note that both usernames and passwords are case-sensitive in Unix.

> My root password still works"Your" root password ?
You don't have one, and by default, root doesn't have a password either - the root  account is prohibited from logging in.

I am going to assume you actually mean your password here - which is proof that it is still good.

>  - I can open a Failsafe Gnome session OK, open up a terminal and try "startx", which gets me to the login manager again.  I've tried installing KDM as well, then selecting "KDE" from the login manager, but get the same problem.

I've been trying to fix this for 2 days and being faily new to Ubuntu I'm completely lost...  How do I solve this?  Is there a way to log on as root, and change my user-id password from the terminal?  Or is there a process running somewhere thats locked me out, that I can kill somewhere?  Any help or wisdom very gratefully received!! :D There are many things one can do - the first would be to hit CTRL-ALT-F1 and log in on the text console.
The login theme to use is set in /etc/gdm/gdm.conf, under the key **GtkTheme=**
The themes are in **/usr/share/themes/**
If either of those are corrupted you may get problems.

I would start by setting the theme back to Human (the default) and restarting gdm:
> sudo nano /etc/gdm/gdm.conf [FONT=Courier New](search for GtkTheme and set it to Human)[/FONT]> sudo /etc/init.d/gdm restart

---

### Post by eggdeng on 2007-01-01
When you boot, the grub menu should offer you an ubuntu recovery mode which enables you to log on as root. If you set a password for the root account, you should be able to log on as root in graphical mode. Try ```
sudo passwd root
```

---

### Post by itsjustarumour on 2007-01-01
adaptr - thanks for your comments, problem (more or less) solved!  And apologies if my description wasn't too clear, I'm still getting to grips with the terminolgy.  I was 100% certain that my userid/password were correct, so I followed your advice on editing the gdm.conf file (I never knew how to do that).  Strangely, the Gtk Theme key was set to "Human" already (my old login theme was called "Tux" something or other but I couldn't find a mention of that).  But I did spot another key for password-less login at startup, so I changed that one to "TRUE".  I typed sudo /etc/init.d/gdm restart , but it told me it couldn't do this as GDM wasn't the default.  So I tried sudo /etc/init.d/kdm restart , and this brought up a Kubuntu/KDE login box which accepted my password and got me to my Desktop.  So thanks very much for the advice, I don't understand half of whats been going on here but I'm VERY happy now that I can access all my stuff again! :D  All I need to do now is work out how to get my normal Gnome login screen back...

eggdeng  -cheers for your comment, but problem sorted!  :)

---

### Post by itsjustarumour on 2007-01-01
Quick update - I've now uninstalled all KDE components, and am back where I started before things went wrong!  Have my original login screen back, and password working fine...  :)

---

