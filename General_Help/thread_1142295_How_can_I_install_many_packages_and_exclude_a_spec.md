---
title: "How can I install many packages and exclude a specific one?"
date: 2009-04-29
forum: General Help
---

### Post by Pidgin on 2009-04-29
I have a task to do. This task is to install a bunch of packages. You see, by default APT will install all recommended packages. But among those recommended packages, one specific package cannot be installed, or things will be messed up. How can I achieve that?
Synaptic Package Manager is not available, because I can only use command-line interface while performing the task.
Thank you!

---

### Post by CatKiller on 2009-04-29
sudo apt-get --no-install-recommends install <bunch of packages>

should so it.

---

### Post by Pidgin on 2009-04-30
> **CatKiller said:**
> sudo apt-get --no-install-recommends install <bunch of packages>

should so it.

Thank you!
But I mean that all recommended packages should be installed except for only one.

---

### Post by mb_webguy on 2009-04-30
Is there some reason you couldn't install everything, then uninstall the single unwanted package?

---

### Post by Pidgin on 2009-04-30
> **mb_webguy said:**
> Is there some reason you couldn't install everything, then uninstall the single unwanted package?

Yeah. Once it starts to configure that unwanted package, the system will be messed up.

---

### Post by CatKiller on 2009-04-30
> **Pidgin said:**
> Thank you!
But I mean that all recommended packages should be installed except for only one.

Dependencies would still be installed. Recommended packages are just those that are assumed to be part of the same function. So, for example, gimp suggests gimp-help, but gimp-help is not necessary for gimp to function. You could then include the recommended packages that you **do** want in your install command along with <bunch of packages>.

If you've already got a version of the suspect package installed, you can lock the version of that package to stop it being upgraded. If you use aptitude rather than apt-get, you can use the **forbid-version** command to stop that version of the suspect package being installed at all.

For that matter, you could probably just use aptitude to do what you want directly. It's a command-line program, but it does have an ncurses interface.

---

### Post by Pidgin on 2009-05-01
> **CatKiller said:**
> Dependencies would still be installed. Recommended packages are just those that are assumed to be part of the same function. So, for example, gimp suggests gimp-help, but gimp-help is not necessary for gimp to function. You could then include the recommended packages that you **do** want in your install command along with <bunch of packages>.

If you've already got a version of the suspect package installed, you can lock the version of that package to stop it being upgraded. If you use aptitude rather than apt-get, you can use the **forbid-version** command to stop that version of the suspect package being installed at all.

For that matter, you could probably just use aptitude to do what you want directly. It's a command-line program, but it does have an ncurses interface.

Thank you for your patient explanation!
I know the difference between dependencies and recommendations. But there are hundreds of recommended packages needed to be installed, except for only one.

---

