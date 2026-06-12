---
title: "I like 6.06 LTS"
date: 2006-09-25
forum: Desktop Environments
---

### Post by jgcamp99 on 2006-09-25
But the upcoming Edgey Eft will have a new gnome and not to mention Evolution . Will Dapper update to this as well via repositories or will we have to download Edgey Eft and upgrade to it via some option to upgrade in the installation of that live cdrom ? The volatility of changes with Linux, kinda makes 5 year support (LTS) really a matter of upgrading to Edgey Eft ?

I'd hate to have to start over with a clean install to get all the latest and greatest features Edgey will have. I'm wondering how many of the applications new OS Edgey Eft will break that currently works in Dapper ?

---

### Post by Rule on 2006-09-25
dapper will not have the new gnome and evolution but the upgrade is very simple just open up your /etc/apt/sources.list file with you favorite text-editor and change "dapper" to "edgy" then just "sudo aptitude update" then "sudo aptitude dist-upgrade" and your all set 8)

---

### Post by sarhento_lobo on 2006-09-25
Right, but before you do that, make sure to browse the forums for how other users' experience of upgrading went. Then if you think you're brave enough, go for it! ;)

At any rate, one thing I'm excited about with the new gnome is compositing effects, but I'm too lazy/scared to try and upgrade. What I did was I set up aiglx/compiz and it's amazing, I can't imagine anything on the horizon right now that will make me change my installation. You might want to try it too ;)

---

### Post by az on 2006-09-25
> **jgcamp99 said:**
> But the upcoming Edgey Eft will have a new gnome and not to mention Evolution . Will Dapper update to this as well via repositories or will we have to download Edgey Eft and upgrade to it via some option to upgrade in the installation of that live cdrom ?

When Edgy is released, the update-manager will have an extra button for you to press which will doo all the work to dist-upgrade your system to it.

You will have the choice of staying with the LTS Dapper release or upgrading to Edgy - it will be your choice.  But you will not have to reinstall unless you want to.

> **jgcamp99 said:**
> 
 The volatility of changes with Linux, kinda makes 5 year support (LTS) really a matter of upgrading to Edgey Eft ?

Actually, it's three years on the desktop and five years on the server.

> **jgcamp99 said:**
> 
I'd hate to have to start over with a clean install to get all the latest and greatest features Edgey will have. I'm wondering how many of the applications new OS Edgey Eft will break that currently works in Dapper ?

Nothing should break because of the dist-upgrade (once released), but Edgy will have more cutting-edge features which means newer applications wich has not been tested as much as the stuff Dapper has (or had at release time).

---

