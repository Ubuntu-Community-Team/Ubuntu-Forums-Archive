---
title: "New to Linux, but have a few concerns."
date: 2005-08-12
forum: Desktop Environments
---

### Post by twilager on 2005-08-12
I recently started being bored with my computer at home.  Decided I wanted to get a laptop.  So i bought a cheap NX6110 from HP Compaq.  Decided to try and install linux for something interesting to do while im at work.  

I have installed ubuntu and kubuntu a few times now.  I have even got my wireless card going with linuxant.  But for the life of me I cant get a decent MSN/YAHOO messenger client installed and working.  Thats like all i care about.  I can use the original software on the cd for most everything else.

Anyone have some readme or tutorials for installing certain things on ubuntu.  altoguh i installed the package for GCC freeciv says its not installed.  KUBUNTU is frustrating.

---

### Post by questionasker on 2005-08-12
[QUOTE=twilager]I recently started being bored with my computer at home.  Decided I wanted to get a laptop.  So i bought a cheap NX6110 from HP Compaq.  Decided to try and install linux for something interesting to do while im at work.  

I have installed ubuntu and kubuntu a few times now.  I have even got my wireless card going with linuxant.  But for the life of me I cant get a decent MSN/YAHOO messenger client installed and working.  Thats like all i care about.  I can use the original software on the cd for most everything else.

Anyone have some readme or tutorials for installing certain things on ubuntu.  altoguh i installed the package for GCC freeciv says its not installed.  KUBUNTU is frustrating.[/QUOTE]
 huh... thats weird...

either Kopete (that comes with Kubuntu, even though i dont ever use it) or Gaim should work fine...

---

### Post by palsyboy on 2005-08-12
I also highly recommend Gaim.

---

### Post by Lord Illidan on 2005-08-12
Have you read the Ubuntu Guide? [www.ubuntuguide.org](www.ubuntuguide.org) 
Also, I recommend using synaptic and installing the gcc compiler from there.
And tell us what error message freeciv is returning, don't be vague...

---

### Post by shakin on 2005-08-12
Since you are on the Kubunto forum, I assume you are using KDE. Try Kopete. I currently have it setup to use ICQ and MSN, but it does Yahoo as well. Nice client.

You should install build-essential, which will install GCC and all the other things needed to compile a program.

---

### Post by GeneralZod on 2005-08-12
[QUOTE=twilager]altoguh i installed the package for GCC freeciv says its not installed. [/QUOTE]

FreeCiv should be in the repositories - generally speaking, most of the software you could ever want are stored in the repositories, and it is extremely rare that you will need to compile from source.   Make sure universe etc are added (read the section on adding respositories in the Ubuntu guide), do

```
apt-get install synaptic

```

to get a decent GUI package manager, open up synaptic (should be in the System menu, if I recall), click "Reload", then search for freeciv and any other programs you want (e.g. gaim, Firefox, etc), right-click on each, select install and then, once you've chosen all the software you want, click Apply and sit back and relax while Synaptic downloads and installs everything you want :)

---

### Post by skyboy on 2005-08-12
Kopete, gaim are just fine and work both on gnome and kde.
If you want to give a try to another msn chat client with Video, try mercury at [http://mercury.to/](http://mercury.to/)
it's still in big dev but it's a Java client and very nice indeed.

---

### Post by greghill on 2005-08-12
I was never big on chat until recently when my sister in law needed a walk through on her new Ubuntu installation. I installed amsn through synaptic, logged on through my hotmail account and it worked flawlessly. Give that a try if you want msn chat. Not sure if it works for Yahoo, though. Like I said, I'm very new to this chat stuff. :)

---

