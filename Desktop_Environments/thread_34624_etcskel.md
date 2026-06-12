---
title: "/etc/skel"
date: 2005-05-15
forum: Desktop Environments
---

### Post by Euphoric Nightmare on 2005-05-15
I want to copy all of my current user's information to the directory /etc/skel

I am having problems with this.

if i do this:
cp -R /~/ /etc/skel

it is not copying all the .* files for some reason.  Can someone help out with this?  In addition, do I need to do some other things to work out permission issues?

---

### Post by JonahRowley on 2005-05-15
Don't copy all of your files into **/etc/skel**, be selective.  A lot of things don't belong there.

You are running the cp command under sudo, right?  Also, that **/~/** was a typo, right?  It should be **~/**.  As for the permissions, it doesn't really matter.  They should be owned by root and have all the permissions you want the files to have in new user's home directories.  Other than that, they can be anything you want them to be.

---

### Post by Euphoric Nightmare on 2005-05-15
[QUOTE=JonahRowley]Don't copy all of your files into **/etc/skel**, be selective.  A lot of things don't belong there.

You are running the cp command under sudo, right?  Also, that **/~/** was a typo, right?  It should be **~/**.  As for the permissions, it doesn't really matter.  They should be owned by root and have all the permissions you want the files to have in new user's home directories.  Other than that, they can be anything you want them to be.[/QUOTE]

Yes it is ~/.  Which files do I put there?  or is it just preference?

---

### Post by JonahRowley on 2005-05-16
I would avoid putting your gnome config files in /etc/skel, and certainly things like **.bash_history** and **.ssh/**.

---

