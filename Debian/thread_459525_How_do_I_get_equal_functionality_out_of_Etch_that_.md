---
title: "How do I get equal functionality out of Etch that we enjoy in Ubuntu?"
date: 2007-05-30
forum: Debian
---

### Post by MetalMusicAddict on 2007-05-30
Last time I installed Etch I noticed that the number of packages available was very small compared to Ubuntu.

So from anyone using Etch Id like to know what additional repos you use?

---

### Post by Pobega on 2007-05-30
main, contrib and non-free.

Debian has way more packages than Ubuntu, even in just main, so I don't see how you can say that Ubuntu has more packages available than Debian.

---

### Post by kerry_s on 2007-05-30
i moved mine to lenny/sid, but here's my list anyways. :p

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main contrib non-free 
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib non-free 
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free   
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free 
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main

---

### Post by MetalMusicAddict on 2007-05-30
> **Pobega said:**
> main, contrib and non-free.

Debian has way more packages than Ubuntu, even in just main, so I don't see how you can say that Ubuntu has more packages available than Debian.

No, by default Etch has about 1200 packages available. Ubuntu has over 20k. This is what I'm looking to change.

Thanx kerry_s. Ill look over it.

I do want to stay with repos and packages made JUST for Etch though.

---

### Post by kerry_s on 2007-05-31
just chage them all to stable.

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) stable main contrib non-free 
deb [http://security.debian.org/](http://security.debian.org/) stable/updates main contrib non-free 
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free 
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

mine has 21000+ in the repo

---

### Post by Pobega on 2007-05-31
> **MetalMusicAddict said:**
> No, by default Etch has about 1200 packages available. Ubuntu has over 20k. This is what I'm looking to change.

Thanx kerry_s. Ill look over it.

I do want to stay with repos and packages made JUST for Etch though.

1,200 packages...?

Are you sure you used Debian? Debian has more packages than Ubuntu, and that's a fact. 

[http://packages.debian.org/testing/allpackages.en.txt.gz](http://packages.debian.org/testing/allpackages.en.txt.gz)

This is everything in testing. According to SciTe, there are 23,353 packages in that list. And there are even more packages in Sid.

According to [http://packages.ubuntu.com/feisty/allpackages.en.txt.gz](http://packages.ubuntu.com/feisty/allpackages.en.txt.gz), Ubuntu has 21,528 packages in it's repositories.

---

### Post by MetalMusicAddict on 2007-05-31
> **Pobega said:**
> 1,200 packages...?

Are you sure you used Debian? Debian has more packages than Ubuntu, and that's a fact. 

[http://packages.debian.org/testing/allpackages.en.txt.gz](http://packages.debian.org/testing/allpackages.en.txt.gz)

This is everything in testing. According to SciTe, there are 23,353 packages in that list. And there are even more packages in Sid.

According to [http://packages.ubuntu.com/feisty/allpackages.en.txt.gz](http://packages.ubuntu.com/feisty/allpackages.en.txt.gz), Ubuntu has 21,528 packages in it's repositories.

Your not reading what I'm saying. "By default" ;)

On a clean Etch install your sources list looks like:

```
[SIZE="1"]#deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 CD Binary-1 20070407-11:55]/ etch contrib main

deb http://security.debian.org/ etch/updates main contrib
deb-src http://security.debian.org/ etch/updates main contrib[/SIZE]
```

I had to add every thing in red.

So now it looks like:
```
[SIZE="1"]#deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 CD Binary-1 20070407-11:55]/ etch contrib main

[COLOR="Red"]deb http://ftp.us.debian.org/debian etch main contrib non-free
deb http://www.debian-multimedia.org etch main[/COLOR]

deb http://security.debian.org/ etch/updates main contrib
deb-src http://security.debian.org/ etch/updates main contrib

#Beryl

[COLOR="Red"]deb http://debian.beryl-project.org/ etch main[/SIZE]
```[/COLOR]
And that still only gives me 18,803 packages. "By default" Ubuntu has access to more packages OTB. Period. Users HATE going through this. I'm used to it and it took me a bit to find the repos. Hell,  **deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main** should be part of non-free afaic.

And why would you try to compare # of packages Etch doesnt use? ie Testing. Completely unhelpful.

Remember more people are going to be looking at this thread really looking for a answer and you've provided no help.

Help would have been providing equivalent repo additions specifically for Etch which kerry_s has done.

So. To get back on topic...

How do I get equal functionality out of Etch that we enjoy in Ubuntu? "repo-wise"?

So far:
```
[SIZE="1"]#deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 CD Binary-1 20070407-11:55]/ etch contrib main

deb http://ftp.us.debian.org/debian etch main contrib non-free
deb http://www.debian-multimedia.org etch main

deb http://security.debian.org/ etch/updates main contrib
deb-src http://security.debian.org/ etch/updates main contrib

#Beryl
deb http://debian.beryl-project.org/ etch main[/SIZE]
```

---

### Post by ThinkBuntu on 2007-05-31
I didn't mind...ten seconds of editing is worth thousands of free packages. Imagine the work you do to buy one piece of sophisticated software...

---

### Post by MetalMusicAddict on 2007-05-31
> **ThinkBuntu said:**
> I didn't mind...ten seconds of editing is worth thousands of free packages. Imagine the work you do to buy one piece of sophisticated software...

Oh sure. Totally. I'm just trying to get this together for people who are used to Ubuntu that want to try Debian Etch. ;)

---

### Post by ThinkBuntu on 2007-05-31
> **MetalMusicAddict said:**
> Oh sure. Totally. I'm just trying to get this together for people who are used to Ubuntu that want to try Debian Etch. ;)
Yeah, I'm more patient than most users (not implying you) with package management which is why YaST hasn't been a problem for me. The only package system with intolerable slowness for me was portage. And yep, I know that some apps have binaries through Portage, but not all.

---

### Post by tturrisi on 2007-05-31
> How do I get equal functionality out of Etch that we enjoy in Ubuntu? 
Please defing "equal functionality".
AFAIC, a straight debian install has way more functionality than Ubuntu.  But ubuntu has more apps installed by default, but IMHO the majority are unneeded unnecessary bloat.  For example, you'll get a much faster efficient system if jsut install the etch net install and uncheck all software on the page in the installer.  This give just the base system.  Then reboot, login and install just what you want from the ground up.  If want Gnome, then do apt-get install xorg gnome-core and do NOT install gnome-desktop-environment, the equivilant of the ubuntu-desktop package.

---

### Post by Pobega on 2007-05-31
> **MetalMusicAddict said:**
> Your not reading what I'm saying. "By default" ;)

On a clean Etch install your sources list looks like:

```
[SIZE="1"]#deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 CD Binary-1 20070407-11:55]/ etch contrib main

deb http://security.debian.org/ etch/updates main contrib
deb-src http://security.debian.org/ etch/updates main contrib[/SIZE]
```

I had to add every thing in red.

So now it looks like:
```
[SIZE="1"]#deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 CD Binary-1 20070407-11:55]/ etch contrib main

[COLOR="Red"]deb http://ftp.us.debian.org/debian etch main contrib non-free
deb http://www.debian-multimedia.org etch main[/COLOR]

deb http://security.debian.org/ etch/updates main contrib
deb-src http://security.debian.org/ etch/updates main contrib

#Beryl

[COLOR="Red"]deb http://debian.beryl-project.org/ etch main[/SIZE]
```[/COLOR]
And that still only gives me 18,803 packages. "By default" Ubuntu has access to more packages OTB. Period. Users HATE going through this. I'm used to it and it took me a bit to find the repos. Hell,  **deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main** should be part of non-free afaic.

And why would you try to compare # of packages Etch doesnt use? ie Testing. Completely unhelpful.

I should've used Etch, yeah, I didn't think about that. But as of now Etch and Lenny are almost identicle, minus a few packages removed due to RC bugs (I'm not sure on the total count, but it can't be any more than 100)

Also, just as a note, I personally don't advise using Debian stable for personal use; Upgrading from one Debian release to the next release is a lot of hard work (Due to the large time gap), and sticking with testing as a rolling release is generally less hassle, and more up to date. In a year from now, while Firefox is on version 2.4.0.3, you'll be stuck with 2.0.0.3.


**Edit:** As for debian-multimedia being in non-free, that isn't possible. The reason that the things hosted on debian-multimedia aren't in non-free is because they're illegal in some (most?) places, and non-free is only for proprietary/closed source software; Illegal software is not allowed in non-free.

---

### Post by MetalMusicAddict on 2007-05-31
Jesus doesn't anyone read the threads?

> **tturrisi said:**
> Please defing "equal functionality".
I did. Read the thread.
> AFAIC, a straight debian install has way more functionality than Ubuntu.  But ubuntu has more apps installed by default, but IMHO the majority are unneeded unnecessary bloat.  For example, you'll get a much faster efficient system if jsut install the etch net install and uncheck all software on the page in the installer.  This give just the base system.  Then reboot, login and install just what you want from the ground up.  If want Gnome, then do apt-get install xorg gnome-core and do NOT install gnome-desktop-environment, the equivilant of the ubuntu-desktop package.

I can do this in Ubuntu as well.

---

### Post by tturrisi on 2007-06-01
I did read the thread!
Apparantly you are asking how to enable Etch to have the same amount of software packages available as Ubuntu on a default install?

Well, I've not run (nor wanted to) Ubuntu in quite some time, but last time I installed Dapper, Ubuntu had far less available packages than Etch by default.  The universe & multi-universe ubuntu repos were not enabled by default.  As for functionality, on Etch, one can always install Synaptic and add additional repos once one knows the sources for them.

debian-multimedia is "non functionality" anyway as one still needs to apt-key add the necessary gpgp key in both Ubuntu & Debian.  There's no functionality friendly way of avoiding that.

Ubuntu is about "ease & functionality" for the beginner whereas Debian is more about choice.  One can do a Debian install and have a choice of what gets installed completely, Ubuntu has little choice on the installation.  One ends up w/ Ubuntu, removing unwanted packages unless use the alternative cd.  An Etch net-install can install Etch, Lenny or Sid too.

---

### Post by webmonkey44 on 2007-06-22
I'd check what repos you have.

---

### Post by deanlinkous on 2007-06-22
A standard default debian install should include the main repos and the security repos afaik.
And I dont recall all repos being enabled in ubuntu install either.

What equal functionality are you looking for? I must of missed the definition... :D

---

