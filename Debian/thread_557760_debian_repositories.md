---
title: "debian repositories"
date: 2007-09-23
forum: Debian
---

### Post by Ozeuss on 2007-09-23
well, wondering about a couple of things.
I scanned through the package listing of ubuntu and debian- it seems that even now (after 8 months or so) feisty packages are still newer than testing. Am i mistaken?
gutsy will come out with gnome 2.20, and i was wondering when to expect it in sid, or testing.

---

### Post by kerry_s on 2007-09-23
you know gnome is just a meta package right. the 2.20's are already in sid that's why they will be in gutsy, gutsy is just a snap shot of sid, a frozen moment in time.

---

### Post by Ozeuss on 2007-09-23
> **kerry_s said:**
> you know gnome is just a meta package right. the 2.20's are already in sid that's why they will be in gutsy, gutsy is just a snap shot of sid, a frozen moment in time.
Hi Kerry, yeah i know its a meta package, it seems that not all are 2.20- like nautilus, gedit, gdm, epiphany. also, i would probably rather wait until gnome-core hits 2.20, instead of trying to upgrade packages seperately..
If you're already on this thread, may i ask you- how often are you using sid packages? are you using 'testing' as base?

---

### Post by kerry_s on 2007-09-23
i have all the repos and i'm fully updated with sid. i'm using a debian base install + xfce4 buildup, i wouldn't recommend using sid unless you know your way around, it has a habit of throwing some curves, lost vlc 2 days ago, i have mplayer so no biggy there.

normally i just use etc/lenny when i need a dependable system. i use sid when i get bored and like to see what could happen next. ;)

yeah, waiting for all the gnome stuff is a good idea, i bet you gutsy is using a mix of both, that's probably why there have been so many gutsy posts.

my sources.list->

```

deb http://ftp.debian.org/debian/ etch main contrib non-free 
deb http://ftp.debian.org/debian/ lenny main contrib non-free 
deb http://ftp.debian.org/debian/ sid main contrib non-free  
deb http://www.debian-multimedia.org/ sid main  

# su
# gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# gpg --armor --export  6A423791| apt-key add -
deb http://deb.opera.com/opera/ sid non-free 
deb http://deb.opera.com/opera-beta/ unstable non-free 

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

# deb-src http://ftp.debian.org/debian/ etch main contrib non-free 
# deb-src http://security.debian.org/ etch/updates main contrib non-free 
# deb-src http://ftp.debian.org/debian/ lenny main contrib non-free 
# deb-src http://security.debian.org/ lenny/updates main contrib non-free 
# deb-src http://ftp.debian.org/debian/ sid main contrib non-free 

```

---

### Post by Ozeuss on 2007-09-23
ok, great. thanks.

---

