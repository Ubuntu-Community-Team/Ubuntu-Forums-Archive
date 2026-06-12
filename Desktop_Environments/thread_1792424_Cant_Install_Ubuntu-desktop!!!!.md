---
title: "Cant Install Ubuntu-desktop!!!!"
date: 2011-06-28
forum: Desktop Environments
---

### Post by subchief on 2011-06-28
[B]Help,
i was running a routine update via synaptic package manager and decided to upgrade nautilus-data
i was informed via a dialogue box that the following applications were going to be removed;
1. gnome session
2. nautilus
3. nautilus-share
4. ubuntu-desktop
so after running the upgrade, i tried to reinstall these applications and none of them will install!!!
I get an error message saying about unsatisfiable dependencies with nautilus-data!!!
i tried to run a partial upgrade but that resulted in an error message saying;
"Cant install 'Ubuntu-Desktop'
it was impossible to install a required package. please report this as a bug"

can anyone help please...I cant shutdown my machine as i wouldn't be able to log back into my desktop!!!

I am running Ubuntu Lucid.

Thanks!!!!
[/B]

---

### Post by subchief on 2011-06-28
> **subchief said:**
> [B]Help,
i was running a routine update via synaptic package manager and decided to upgrade nautilus-data
i was informed via a dialogue box that the following applications were going to be removed;
1. gnome session
2. nautilus
3. nautilus-share
4. ubuntu-desktop
so after running the upgrade, i tried to reinstall these applications and none of them will install!!!
I get an error message saying about unsatisfiable dependencies with nautilus-data!!!
i tried to run a partial upgrade but that resulted in an error message saying;
"Cant install 'Ubuntu-Desktop'
it was impossible to install a required package. please report this as a bug"

can anyone help please...I cant shutdown my machine as i wouldn't be able to log back into my desktop!!!

I am running Ubuntu Lucid.

Thanks!!!!
[/B]
  Ok...silly me...was running update using different sources...cd and internet hence the conflict...removing the apton cd as software source then running "sudo apt-get install ubuntu-desktop" did the trick!!!

---

