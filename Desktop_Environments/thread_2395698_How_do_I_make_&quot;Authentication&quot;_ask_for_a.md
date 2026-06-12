---
title: "How do I make &quot;Authentication&quot; ask for a username instead of drop down menu?"
date: 2018-07-05
forum: Desktop Environments
---

### Post by tuesday.espresso on 2018-07-05
I have the latest Lubuntu, with all the current updates.

I've been going around my system and changing some settings in the interest of security. With some research, I was able to make the login screen ask for a username instead of having a drop down with a list of all users (including "admin" user).

My question is this:

How do I make it so that when I (as a regular user) want to temporarily have "admin" rights, instead of being asked for the password and having a drop down menu for the identity of all the "admin" accounts I would have to type in both the password AND the identity of an admin account?

An example of where you would do this:

If you try and change the date and time (System tools -> Time and Date). You are unable to change anything until you press the "unlock" button. When you press "unlock", it comes up with a prompt named "Authentication", where it has a drop down menu for the identity, and is asking for a password.

Now, I believe that I have: lxsessions, and lxpolkit.

I tried to look up how to change lxpolkit settings and found this:

[https://wiki.archlinux.org/index.php/Polkit](https://wiki.archlinux.org/index.php/Polkit)

It has a section on changing "Administrator Identities", but it doesn't tell you what options you have available (i.e. what code is a drop down, what code isn't a drop down, what code only allows one identity etc.).

---

### Post by again? on 2018-07-06
I am using Xubuntu 18.04
Don't know if it is possible to allow typing in of a user name instead of a dropdown with the authentication dialog.
I can however limit to a sole user by creating a file /etc/polkit-1/localauthority.conf.d/99-admin.conf 
containing the following (my user is **glen**)
```
[Configuration]
AdminIdentities=unix-user:glen
```

The authentication dialog will then only prompt for a password for the user **glen**.
[ATTACH=CONFIG]280291[/ATTACH]

as opposed to the normal authentication dialog with a user dropdown.
[ATTACH=CONFIG]280292[/ATTACH]

---

