---
title: "Thunderbird problem"
date: 2006-01-17
forum: General Help
---

### Post by paul2005 on 2006-01-17
I recently installed Thunderbird 1.5 which seemed to be working well. However, I couldn't do any auto-updates through it so I ran 'sudo thunderbird' from a terminal and then checked for updates.

Now when I try to run Thunderbird normally (without sudo) it hasn't got my mail accounts setup, just the themes and extensions. If I look in the profiles folder (.thunderbird) then all my mail and account settings still exist, it just seems like Thunderbird doesn't recognise them when it loads up and instead just opens the New Account wizard.

Does anyone know what I might have done by running it as root and how I can fix the problem?

---

### Post by lamego on 2006-01-17
[QUOTE=paul2005]I recently installed Thunderbird 1.5 which seemed to be working well. However, I couldn't do any auto-updates through it so I ran 'sudo thunderbird' from a terminal and then checked for updates.

Now when I try to run Thunderbird normally (without sudo) it hasn't got my mail accounts setup, just the themes and extensions. If I look in the profiles folder (.thunderbird) then all my mail and account settings still exist, it just seems like Thunderbird doesn't recognise them when it loads up and instead just opens the New Account wizard.

Does anyone know what I might have done by running it as root and how I can fix the problem?[/QUOTE]

The Thunderbird 1.5 packaged by mozilla uses .thunderbird for its configuration, the thunderbird which comes  on ubuntu uses .mozilla-thunderbird .

Renaming .mozilla-thunderbird to .thunderbird should work .

---

### Post by kaamos on 2006-01-17
[QUOTE=paul2005]Does anyone know what I might have done by running it as root and how I can fix the problem?[/QUOTE]
Running as root has owned the config files to root. Fix with
```
sudo chown **username**:**username** .thunderbird -R
```

---

### Post by paul2005 on 2006-01-17
Thanks for the suggestion but I tried 'sudo chown paul .thunderbird -R and it didn't make any difference - Thunderbird still opens with no email accounts and so opens the New Account wizard on start-up.

In my .thunderbird folder there's only 1 profile, it's set as the default and it still contains all my settings, themes, extensions and mail folders so I've no idea why Thunderbird won't load them on start up.

---

### Post by kaamos on 2006-01-17
You have to be in your home directory when you use the command and it should be: "sudo chown paul:paul .thunderbird -R". If this does not help, you can try "chmod 777 .thunderbird -R"

---

