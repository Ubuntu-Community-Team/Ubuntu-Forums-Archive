---
title: "[SOLVED] Recorder in Debian Xfce"
date: 2008-06-08
forum: Debian
---

### Post by Inxsible on 2008-06-08
I am trying to install [Recorder]("http://code.google.com/p/recorder/") in Debian xfce and I am getting the following. I am probably missing some libraries, but I cannot say which.```
inxsible@debian:~/recorder-1.3.2$ sudo make install 
install -m 755 -d /bin /share/applications /share/pixmaps 
install -m 644 recorder.png /share/pixmaps 
install -m 644 recorder.desktop /share/applications 
install -m 755 recorder /bin 
for lang in ar cs es fr pt_BR ru it; do \
                 install -m 755 -d /share/locale/$lang/LC_MESSAGES;\
                 install -m 755 -d mo/$lang/LC_MESSAGES;\
                 msgfmt po/$lang.po -o mo/$lang/LC_MESSAGES/recorder.mo;\
                 install -m 644 mo/$lang/LC_MESSAGES/recorder.mo /share/locale/$l
ang/LC_MESSAGES/recorder.mo;\         done 
/bin/sh: line 3: msgfmt: command not found 
install: cannot stat `mo/ar/LC_MESSAGES/recorder.mo': No such file or directory 
/bin/sh: line 3: msgfmt: command not found 
install: cannot stat `mo/cs/LC_MESSAGES/recorder.mo': No such file or directory 
/bin/sh: line 3: msgfmt: command not found 
install: cannot stat `mo/es/LC_MESSAGES/recorder.mo': No such file or directory 
/bin/sh: line 3: msgfmt: command not found 
install: cannot stat `mo/fr/LC_MESSAGES/recorder.mo': No such file or directory 
/bin/sh: line 3: msgfmt: command not found 
install: cannot stat `mo/pt_BR/LC_MESSAGES/recorder.mo': No such file or directory 
/bin/sh: line 3: msgfmt: command not found 
install: cannot stat `mo/ru/LC_MESSAGES/recorder.mo': No such file or directory 
/bin/sh: line 3: msgfmt: command not found 
install: cannot stat `mo/it/LC_MESSAGES/recorder.mo': No such file or directory 
make: *** [install] Error 1 
inxsible@debian:~/recorder-1.3.2$
```Can someone help me out. The packages that are listed on the website are not found by aptitude search. How do I know if they are installed on my machine. which doesn't help. Maybe they haven't mentioned the version numbers of the packages or something.

---

### Post by kerry_s on 2008-06-08
looking at the site it needs to be done as root, so->

[B]sudo -i
make install[/B]

---

### Post by Inxsible on 2008-06-08
> **kerry_s said:**
> looking at the site it needs to be done as root, so->

[B]sudo -i
make install[/B]
I did do it with root. the command i gave was sudo make install


EDIT: Oh and I am also in sudoers

---

### Post by kerry_s on 2008-06-09
> **Inxsible said:**
> I did do it with root. the command i gave was sudo make install


EDIT: Oh and I am also in sudoers

i know that, but it's says you actually got to be "root", not a user with root privileges.(does that make since?) 

with sudo sometimes the command is not past all the way down the line, it's like using a command where you need several sudo's.
not sure how to explain it. :confused:

just give it a go, pretty please. :)

by the way, i just got me a ibm t20 and tried to load lenny, man did it install a lot of gnome crap with synaptic. so you were right there been changes from when i last did it, i also noticed the recommends is always on know.
i think i'm going to try again but starting with etch.

---

### Post by Inxsible on 2008-06-09
> **kerry_s said:**
> i know that, but it's says you actually got to be "root", not a user with root privileges.(does that make since?) 

with sudo sometimes the command is not past all the way down the line, it's like using a command where you need several sudo's.
not sure how to explain it. :confused:

just give it a go, pretty please. :)Hmmm...now that's interesting and strange coming from the Ubuntu world. Alrite, I shall give it a try tonight.

> **kerry_s said:**
> by the way, i just got me a ibm t20 and tried to load lenny, man did it install a lot of gnome crap with synaptic. so you were right there been changes from when i last did it, i also noticed the recommends is always on know.
i think i'm going to try again but starting with etch.Aha !! So I am not alone. Better to go with a business iso + whatever you want.

On a related issue....if I try to install Sonata - for mpd or even firestarter - it tries to install a lot of Gnome packages...I am not sure if its the entire Gnome or not...but there are quite a lot of packages. I just selected No....but I do still need Firestarter and Sonata :(

---

### Post by Inxsible on 2008-06-09
hey kerry,

i tried it as root but still no go. I get the same errors.

---

### Post by kerry_s on 2008-06-10
bummer :(

---

### Post by Arthur Archnix on 2008-06-10
Do you have these dependencies installed? 
> **Depends on:** pygtk, cdrkit or cdrtools, dvd+rw-tools, coreutils and gettext.
I think it's rather silly to install a cd burner that's not already in the repositories. For one, your custom build won't receive updates or testing from the Debian community.

Especially when there is such a range of good options already...
on the gui there is k3b, gnome-baker, brasero, xcdroast,  and xfburn

---

### Post by Inxsible on 2008-06-10
> **Arthur Archnix said:**
> Do you have these dependencies installed? 

I think it's rather silly to install a cd burner that's not already in the repositories. For one, your custom build won't receive updates or testing from the Debian community.

Especially when there is such a range of good options already...
on the gui there is k3b, gnome-baker, brasero, xcdroast,  and xfburnYes Arthur, I do have the dependencies installed.

The motto of installing something that is not in the repos is two-fold
1) I get to learn about different software available
2) this is for a very low end machine with 256 MB Ram and it has fluxbox. I do not want to install k3b or gnome-baker and have all the kde/gnome dependencies installed.

As for updates, I really do not care...since I can update whenever I feel like or when a new release comes out. I don't have to wait until the repos get the new version :)

---

