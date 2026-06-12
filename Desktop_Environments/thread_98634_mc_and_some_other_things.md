---
title: "mc and some other things"
date: 2005-12-03
forum: Desktop Environments
---

### Post by mckemie on 2005-12-03
I just did my first series of 5.10 installs.  After doing a default type install, I found I couldn't get apache to work.  Probably a port closed or something.  How do I control ports?  I did install apache2.

I then went to a "server" install and now apache works fine.

I installed mc and it works fine locally, but not via ssh.  Line drawing characters appear as a series of boxes.  How do I fix/workaround that?

Now, I attempting to get X up on my "server" install.  I'm in the middle of installing gdm and it's dependencies.   Is there some "virtual" package that will get all the basic X stuff installed for me?  Or is there some way to get to the initial "desktop" install stuff?

Is anyone else here using apt-cacher?  Using an older version (.6?), I had trouble mixing regular Debian and Ubuntu; can I expect the same problems with the newer (1.<something>) version  of apt-cacher?

---

### Post by az on 2005-12-03
[QUOTE=mckemie]I just did my first series of 5.10 installs.  After doing a default type install, I found I couldn't get apache to work.  Probably a port closed or something.  How do I control ports?  I did install apache2.[/QUOTE]

If you did not install anything like firestarter, there is no reason why it did not work.

[QUOTE=mckemie]I then went to a "server" install and now apache works fine.[/QUOTE]

I dunno.  

[QUOTE=mckemie]I installed mc and it works fine locally, but not via ssh.  Line drawing characters appear as a series of boxes.  How do I fix/workaround that?[/QUOTE]

It is a UTF bug that has been fixed (I beleive) recently and will make it in Dapper.  I do not know if there is a backport.

[QUOTE=mckemie]Now, I attempting to get X up on my "server" install.  I'm in the middle of installing gdm and it's dependencies.   Is there some "virtual" package that will get all the basic X stuff installed for me?  Or is there some way to get to the initial "desktop" install stuff?[/QUOTE]

Sudo apt-get install ubuntu-desktop
will install the ubuntu desktop.

sudo apt-get install x-window-system-core
will install the basic X stuff.  Do not forget to add xterm, as this is not included in the core.

[QUOTE=mckemie]Is anyone else here using apt-cacher?  Using an older version (.6?), I had trouble mixing regular Debian and Ubuntu; can I expect the same problems with the newer (1.<something>) version  of apt-cacher?[/QUOTE]

Do not mix debian and Ubuntu repos.

---

### Post by mckemie on 2005-12-04
> **azz]If you did not install anything like firestarter, there is no reason why it did not work.[/QUOTE]

Is firestarter part of the "default" install?

[QUOTE=azz]
It is a UTF bug that has been fixed (I beleive) recently and will make it in Dapper.  I do not know if there is a backport.
[/QUOTE]

I think I saw a selection of "usa-utf" or "usa" character codes go by said:**
> 
Sudo apt-get install ubuntu-desktop
will install the ubuntu desktop.

sudo apt-get install x-window-system-core
will install the basic X stuff.  Do not forget to add xterm, as this is not included in the core.


Thanks!

[QUOTE=azz]
Do not mix debian and Ubuntu repos.[/QUOTE]

Do you say that specifically in regard to the operation of apt-cacher?
I know not to use Debian repositories in my Ubuntu systems.  Apt-cacher might reasonably be expected to cache debs for both straight Debian systems as well as various flavors of Ubuntu.

---

### Post by ranf on 2005-12-04
[QUOTE=mckemie]
I installed mc and it works fine locally, but not via ssh.  Line drawing characters appear as a series of boxes.  How do I fix/workaround that?
[/QUOTE]
Search for a thread titled something like "ugly Midnight commander".

---

### Post by mckemie on 2005-12-04
[QUOTE=ranf]Search for a thread titled something like "ugly Midnight commander".[/QUOTE]

HEY!  That fixed it!  Problem solved!  Thanks!

That thread is in the "hardware" forum.

---

