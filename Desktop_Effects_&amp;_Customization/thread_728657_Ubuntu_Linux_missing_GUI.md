---
title: "Ubuntu Linux missing GUI"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by ubuntoexpert on 2008-03-19
I just installed Ubuntu and there is no GUI.  All I get is a text login.

I tried the following commands:

$startx
This program 'startx' is currently not installed.
You can install it by typing: sudo apt-get install xinit
-bash: startx command not found

$ sudo apt-get install xinit
password:  password
Reading package lists.... done
Building dependency tree
Reading state information....done
Package xinit is not available but is referenced by another package.   This may mean that the package is missing, has been obsoleted, or is only available from another source.
However the following packages replace it:
  x11-common

$ sudo apt-get install x11-common
Prompts me to insert my cd
Setting up x11-common

$startx
Same message as before.  I'm back where I began.


How do I get ubuntu to give me a GUI??    Please help, frustration is mounting.

---

### Post by mcduck on 2008-03-19
Did you maybe use the Server install? It doesn't include any GUI by default.

"sudo apt-get install ubuntu-desktop" will install the Gnome desktop and all Ubuntu's default graphical stuff for you. Alternatively use kubuntu-desktp or xubuntu-desktop instead for KDE or XFCE4 desktops.

---

