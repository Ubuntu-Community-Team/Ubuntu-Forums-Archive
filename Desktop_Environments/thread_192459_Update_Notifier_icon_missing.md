---
title: "Update Notifier icon missing"
date: 2006-06-08
forum: Desktop Environments
---

### Post by dotnick on 2006-06-08
I've noticed for about a week now that my update notifier icon is missing.  I've tried running the program from the command prompt, but it said that update-notifier was running.  So then I killed it and tried again.  Instead of getting error messages, the command seemed to hang and nothing happened.  The only thing I've installed since I've noticed this was a few programs available with the Automatix program.

---

### Post by Trab on 2006-06-08
try going to synaptic and reinstalling update-manager and update-notifier 
(use the search function to find them...)
cheers
Trab

---

### Post by Nano Geek on 2006-06-08
[QUOTE=Trab]try going to synaptic and reinstalling update-manager and update-notifier 
(use the search function to find them...)
cheers
Trab[/QUOTE]Or, type```
sudo apt-get remove update-manager update-notifier
sudo apt-get install update-manager update-notifier
```

---

### Post by dotnick on 2006-06-08
Oddly enough that fixed it.  I don't think I uninstalled both of them before, but I did try doing a reinstall before.  There was a third application uninstalled when called gnome-apps-installer, or something like that.  It didn't get reinstalled. Oh well, I don't need that anyways.  Thanks for the help.

---

