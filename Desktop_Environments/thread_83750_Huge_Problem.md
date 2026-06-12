---
title: "Huge Problem"
date: 2005-10-29
forum: Desktop Environments
---

### Post by kapa_des on 2005-10-29
The intalletion of vaklnut deleted my Gnome Desktop and now I have now Desktop for my OS ... and when i log myself with root with #su it dosen't let me ... how do I activate my Root user ... or what sude I du? so I can type apt-get install Gnome or KDE

---

### Post by kapa_des on 2005-10-29
help here ppl ... plz :(( ...

---

### Post by NewbieNik on 2005-10-29
sudo passwd root

then enter your password then the root password you want twice.
Then su into root using the new password

Hope that helps

---

### Post by matw on 2005-10-29
I assume you can log in as yourself. Correct?

It seems like you can not get "$ su -" to run. True?

Try something like this

$ sudo apt-get install package_name

where package name is something like gnome or gnome-terminal.

---

### Post by clearnitesky on 2005-10-29
[QUOTE=NewbieNik]$ sudo passwd root

then enter your password then the root password you want twice.
Then su into root using the new password[/QUOTE]

yeah, that's right, then for GNOME: 
# apt-get install ubuntu-desktop

or if you want KDE:
# apt-get install kubuntu-desktop

---

### Post by kapa_des on 2005-10-29
it dosen't work : sudo passwd root ... Password: ... Login Incorrect ...

---

### Post by kapa_des on 2005-10-29
Or what do you mean by "type your passowrd that the root" ... what's my passowrd ... I mean what password?

---

### Post by clearnitesky on 2005-10-29
sorry, take the word root off that.
Type this:

$ sudo passwd

it'll then ask for your password and when you enter it then it'll respond with:

Enter new UNIX password:

The password you then enter should be the one you want to be root's password

---

### Post by matw on 2005-10-29
If I recall correctly

$ sudo passwd root
Old Password: <type in your normal password here>
New Passwrd: <a password for the root user>
New Password: <the same password for the root user>

---

### Post by kapa_des on 2005-10-29
yes but Ubuntu dosen't see my root passowrd under any situations ... when I had Gnome I openned from the meniu New Root Knsole and there it accepted my Password ... but with su or sudo it's dosen't see it ... someone told me that Ubuntu dosen't have active the Root user or smth like that ... well what should I do?

---

### Post by clearnitesky on 2005-10-29
This is *the way* to **set** your *root* password.

when you do "sudo passwd" you have to enter **your** password first, and it'll ask you for a password to use for the "su" command.

---

### Post by NewbieNik on 2005-10-29
This is part of the "beauty" of Ubuntu, it doesn't show a root user as a normal user from the standard install, thus stopping people from logging on as root as a standard user, thus improving security. If you need to "root" something, you use su.

From a generic install root has no password, but to access some of the sudo functions you need to re-enter the users password.

So when you "sudo passwd root" you enter your current password to activate the sudo

passwd root then changes or sets the root password so you enter it, once to tell Ubuntu the password and twice to confirm no spelling mistakes.

It took me a while to get used th the root/su functions, but it makes sense when you consider it!

---

