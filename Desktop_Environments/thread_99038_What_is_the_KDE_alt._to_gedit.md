---
title: "What is the KDE alt. to gedit?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by orev on 2005-12-04
To edit conf files in ubuntu I always used sudo gedit.  I just did a fresh install of kubuntu and the command gedit does not exist, what do I use??

10000 thanks.

---

### Post by 23meg on 2005-12-04
it's Kate.

---

### Post by Seth on 2005-12-04
But don't **sudo kate**, make sure and use **kdesu kate** or you won't be able to log in to KDE.

---

### Post by HermanAB on 2005-12-04
kedit

---

### Post by Adrian on 2005-12-04
[QUOTE=orev]To edit conf files in ubuntu I always used sudo gedit.  I just did a fresh install of kubuntu and the command gedit does not exist, what do I use??

10000 thanks.[/QUOTE]

kwrite is nice also.

...and use "kdesu" instead of "sudo" if you get problems :)

---

### Post by t2kburl on 2005-12-05
I found it more efficient to just

 sudo apt-get install gedit

then you can copy & paste commands

---

### Post by guice on 2005-12-05
vim
:syntax on

FTW (sorry, thread was missing a vi post. :mrgreen:)

---

### Post by metoo on 2005-12-05
Just to add another alternative and to irritate you :-) , you can use mc (midnight commander), F4 is the editor.

---

### Post by z-vet on 2005-12-05
I use nano or MC&#180;s built-in editor.

---

### Post by Freddy on 2005-12-05
A piece of paper and a large hammer :)

---

### Post by GameManK on 2005-12-05
sudo kedit
or
sudo kwrite
in my experience, you only need kdesu when running from the run.. dialog because then it has nowhere to ask you for a password if you do sudo.  in a konsole, sudo works just fine.

kate is nice and has a lot of features that you usually won't need when you just want to change one line in a config file, and it takes an extra second to load.

---

### Post by atoponce on 2005-12-05
[quote=Seth]But don't **sudo kate**, make sure and use **kdesu kate** or you won't be able to log in to KDE.[/quote]

Interesting.  Why?  Not that I doubt you, but I have never tried, and I am curious why running 'sudo kate' would disable your login.  Would 'sudo kwrite' do the same thing?

---

### Post by aysiu on 2005-12-05
I don't know if ```
sudo kate
``` disables login, but I know it doesn't work. ```
sudo kwrite
``` works just fine, though.

---

### Post by atoponce on 2005-12-05
[quote=aysiu]I don't know if ```
sudo kate
``` disables login, but I know it doesn't work. ```
sudo kwrite
``` works just fine, though.[/quote] I wonder, then, if it is a version thing that has been resolved in 5.10 Breezy.  I did have an issue logging in to KDE when I installed Gnome, but I simply modified the permissions on my ~/.ICEauthority file to allow writing by the owner (sudo chmod 600 .ICEauthority), and I have since been able to login just fine.

---

