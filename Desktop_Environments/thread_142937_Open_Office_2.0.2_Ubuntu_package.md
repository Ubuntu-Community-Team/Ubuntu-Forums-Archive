---
title: "Open Office 2.0.2 Ubuntu package"
date: 2006-03-11
forum: Desktop Environments
---

### Post by ubtpenguin on 2006-03-11
Hey guys, 

Openoffice changed openoffice install package to rpm.

I don't know if it is safe to install 2.0.2 rpm over current openoffice 1.9.129 deb.

And do you guys know any ubuntu package of openoffice 2.0.2?

I searched over the web and it didn't exist.

Thanks

---

### Post by RikoW on 2006-03-11
hi,

i removed the openoffice 1.9.x package which came with Ubuntu using Synaptic.

Then I downloaded OOo2.0 from the openoffice web site, converted the .rpm to .deb using alien and installed the .debs using dpkg. worked flawlessly!

Cheers,

             Riko

---

### Post by ubtpenguin on 2006-03-11
Thanks a lot 

cheers~~~

---

### Post by magnusbb on 2006-03-11
First, add this to your /etc/apt/sources.list:
```
deb http://people.ubuntu.com/~doko/OOo2 ./

```

At this time, you will get the 2.0.1 version. But if you are patient enough to wait a few days / weeks, you will get a smooth 2.0.2 Ubuntu version from there.

---

### Post by ubtpenguin on 2006-03-11
wow more thanks

I think I am patient enough to wait.

\\:D/

---

### Post by G_u_s on 2006-03-12
[QUOTE=magnusbb]First, add this to your /etc/apt/sources.list:
```
deb http://people.ubuntu.com/~doko/OOo2 ./

```

At this time, you will get the 2.0.1 version. But if you are patient enough to wait a few days / weeks, you will get a smooth 2.0.2 Ubuntu version from there.[/QUOTE]

i'm sorry, i've tried adding this at the bottom of my sources.list, but when i start Synaptic, it gives the following error message:
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)

it's probably something very noobish from my side, but i can't, for the life of me, figure out what exactly =S

---

### Post by ubtpenguin on 2006-03-12
It worked fine with me

Did you try this
in console?

$>apt-get update

Also, it could be a network problem.

For example, that source site is down for a while.

Try later on.

---

### Post by G_u_s on 2006-03-12
well, thanks, updating worked =) i thought it was automated when launching Synaptic, though... and when i tried going to the URL, it worked fine, so i don't understand.

oh well, it worked, and next time, i'll try manually updating. thanks again =)

---

