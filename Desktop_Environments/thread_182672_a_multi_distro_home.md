---
title: "a multi distro /home?"
date: 2006-05-26
forum: Desktop Environments
---

### Post by dutler on 2006-05-26
Hi,  I have found my self working from kubuntu and suse alot. I have a dual boot machine and am wondering about creating a separate partition to mnt /home for both distros.

i would love to have my kde settings and what no synced in both OSs.

thanks, dutler

---

### Post by aysiu on 2006-05-26
SuSE and Kubuntu may use configuration files differently, so you may end up with a messed up KDE desktop in both systems...

I wouldn't share a /home between the two.

---

### Post by Shay Stephens on 2006-05-26
What if you were running two versions of dapper on the same machine?  Would there still be a problem?

---

### Post by aysiu on 2006-05-26
[QUOTE=Shay Stephens]What if you were running two versions of dapper on the same machine?  Would there still be a problem?[/QUOTE] What do you mean by "two versions" of Dapper? Kubuntu and Ubuntu? That wouldn't be a problem, since they're the same distro.

---

### Post by Shay Stephens on 2006-05-26
Sorry, what I meant was, say I have a main partition loaded with dapper, and a second partition, let's call it "sandbox" also with the same version of dapper.

Could I use the same "home" for both or would that arrangement cause problems?

---

### Post by aysiu on 2006-05-26
[QUOTE=Shay Stephens]Sorry, what I meant was, say I have a main partition loaded with dapper, and a second partition, let's call it "sandbox" also with the same version of dapper.

Could I use the same "home" for both or would that arrangement cause problems?[/QUOTE] You can and should use the same /home for both.

---

### Post by Shay Stephens on 2006-05-26
Su-weeeeeeeeet :D 

Thank you!!!

---

### Post by dutler on 2006-05-27
ya, firgures...
thanks for the help.

does any one have some solutions for gracefully going back and forth tween distros?

-dutler

---

### Post by Jucato on 2006-05-28
[QUOTE=aysiu]You can and should use the same /home for both.[/QUOTE]

Is this really recommended? Wouldn't the configurations for the different apps (the ones in the ~/.kde/share/config folder) conflict with two different KDE-based distros installing configuration files in the same place? or would they have a way of separating them?

---

### Post by aysiu on 2006-05-28
[QUOTE=Fenyx]Is this really recommended? Wouldn't the configurations for the different apps (the ones in the ~/.kde/share/config folder) conflict with two different KDE-based distros installing configuration files in the same place? or would they have a way of separating them?[/QUOTE] If they're both Dapper, they're the same distro.

---

### Post by Jucato on 2006-05-28
Oh I see. sorry for the misunderstanding. I should be reading things more carefully. :p

---

