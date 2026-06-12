---
title: "KreetingKard Installation"
date: 2006-01-05
forum: Desktop Environments
---

### Post by gpeck157 on 2006-01-05
Hi All,

I'm running Ubuntu Breezy not Kubuntu and would like to know if I can install KreetingKard (a KDE program) in Ubuntu without breaking things. I was planning on using "kreetingkard_0.6.0-1_i386.deb" for the installation. Or, is there an equivalent program available for Gnome? Thanks...

---

### Post by audax321 on 2006-01-05
I'm assuming that is the Ubuntu/Kubuntu deb file from [http://linux-life.net/program/cc/kde/app/kreetingkard/dl/](http://linux-life.net/program/cc/kde/app/kreetingkard/dl/)

If so, it should install fine, but you will probably need to install some other KDE packages from the repositories to get it to work. I'm not sure if installing the deb will tell you what dependencies you are missing.

To install the deb file: sudo dpkg -i kreetingkard_0.6.0-1_i386.deb

To remove it, just open up Synaptic, search for it, and tell it to remove it completely (right click the check box and select remove completely).

---

### Post by gpeck157 on 2006-01-05
Thanks audax...

Yes, that's where I got the file. I'll install it and see what happens.

---

### Post by gpeck157 on 2006-01-11
Just a quick update on this...the Kreetingkard file has unmet dependencies. It requires koffice-libs, which also has unmet dependencies. That package requires koffice-data. I've decided to wait for a comparable Gnome app. Also, I did not attempt to install the dependencies using Synaptic. Thanks...

---

### Post by audax321 on 2006-01-12
Are you by any chance installing koffice-libs manually? If you check Synaptic its in there, so you can just install it and all the dependencies should install as well.

---

### Post by gpeck157 on 2006-01-27
[QUOTE=audax321]Are you by any chance installing koffice-libs manually? If you check Synaptic its in there, so you can just install it and all the dependencies should install as well.[/QUOTE]
 
I was using apt-get to install it. I'll try Synaptic when I get my computer back. I'm using my daughter's Windoze machine while my laptop is back at HP getting a new motherboard. 

Also, just before I boxed up my machine to send back to HP, I tried booting Ubuntu, but got a message that my graphical front end was not setup properly and had to be repaired, so all I was able to get was the command line. It was working fine the night before, so I'm not sure what happened.

Thanks...

G

---

