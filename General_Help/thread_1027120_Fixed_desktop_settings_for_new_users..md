---
title: "Fixed desktop settings for new users."
date: 2008-12-31
forum: General Help
---

### Post by albinootje on 2008-12-31
In a few weeks time I need to prepare about 5 Ubuntu computers for new Linux users. 
For them I would like to have fixed desktop settings.
A customized theme, some fixed preferred applications.

Years ago you could put files in /etc/skel/ and those would end up in the home directory of the new user.
Not sure whether it's still all copied from there, as that directory is pretty .. empty by default :)

I also noticed that some of the gnome settings in ~/.gnome2 and ~/.gconf have the name of the user in those configuration files, so just start copying those configuration files over to the home dir of the new users might not be such a wise idea, and leading to errors.

I wonder where and how to give those users fixed settings for the Gnome desktop after I will create/add those new usernames.

Any pointers ?

TIA!

---

### Post by dcstar on 2009-01-01
> **albinootje said:**
> In a few weeks time I need to prepare about 5 Ubuntu computers for new Linux users. 
For them I would like to have fixed desktop settings.
A customized theme, some fixed preferred applications.

Years ago you could put files in /etc/skel/ and those would end up in the home directory of the new user.
Not sure whether it's still all copied from there, as that directory is pretty .. empty by default :)

I also noticed that some of the gnome settings in ~/.gnome2 and ~/.gconf have the name of the user in those configuration files, so just start copying those configuration files over to the home dir of the new users might not be such a wise idea, and leading to errors.

I wonder where and how to give those users fixed settings for the Gnome desktop after I will create/add those new usernames.


[http://www.tuxist.org/pub/get_kde-gnome_desktops_in_line.pdf](http://www.tuxist.org/pub/get_kde-gnome_desktops_in_line.pdf)

---

### Post by albinootje on 2009-01-01
> **dcstar said:**
> [http://www.tuxist.org/pub/get_kde-gnome_desktops_in_line.pdf](http://www.tuxist.org/pub/get_kde-gnome_desktops_in_line.pdf)

A bit ancient that pdf, but thanks for the pointer!

---

