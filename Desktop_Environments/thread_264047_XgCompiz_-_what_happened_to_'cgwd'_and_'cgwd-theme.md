---
title: "Xg/Compiz - what happened to 'cgwd' and 'cgwd-themes'?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by n00b@linux on 2006-09-24
[LEFT]I tried the following code:

```
sudo apt-get install compiz cgwd compiz-gnome xserver-xgl cgwd-themes
```and it came back with

```
Reading package lists... Done
Building dependency tree... Done
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
```Which suggests to me it's not in the repositories.

As it failed at 'cgwd' I ran:

```
sudo apt-get install compiz-gnome xserver-xgl cgwd-themes

```Which came back with:

```
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
E: Couldn't find package cgwd-themes
```Suggesting 'cgwd-themes' is also not in the repositories.

Does anyone know what has happened to both packages?
[/LEFT]

---

### Post by Loffe_ on 2006-09-24
Have you activated QuinnStorm's repositories?

Otherwise add those in Synaptic:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

/Loffe

---

### Post by ayoli on 2006-09-24
these packages aren't anymore in repositories probably due to the transition to beryl, the [quinnstorm fork of compiz]("http://www.compiz.net/topic-4562-1.html")

---

### Post by samssf on 2006-09-24
Yeah, I had the same problem.

Try to get them here:

deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) dapper main

---

### Post by n00b@linux on 2006-09-24
Thanks for the repository details, but neither appears to be there either :(

---

### Post by Dinerty on 2006-09-24
> **n00b@linux said:**
> Thanks for the repository details, but neither appears to be there either :(

[http://www.compiz.net/topic-4690-2.html](http://www.compiz.net/topic-4690-2.html)

Check post #17 for the downloads mate;)

---

### Post by got_nix on 2006-09-24
kinda funny, I configured mine like 1 day before they were removed.. i think i set up mine on tuesday or wednesday of last week 19/09/06, and i had originally planned to setup up a few other things before doing compiz.

---

### Post by btdown on 2006-09-24
How might one get the deb to extract the cgwd themes using fileroller? Could anyone post it?

---

### Post by n00b@linux on 2006-09-24
Thanks for the link, Dinerty.  I had problems with those downloads but I read the whole thread and it pointed me to:

[http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/](http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/)

I followed that thread and seemed to make some progress.

However, I came to the following impass:
```

n00b@ubuntu:~$ startcompiz
gnome-window-decorator: no process killed
/usr/bin/startcompiz: line 5: gnome-window-decorator: command not found
n00b@ubuntu:~$ Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display: 1.0
```Can anyone help me out here?  (I'm beginning to think I'm spinning my wheels with this :()

My /usr/bin/startcompiz file is:
```

#!/bin/sh
killall gnome-window-decorator
wait

gnome-window-decorator &
compiz --replace gconf &
```

---

### Post by Dinerty on 2006-09-24
How about if you

```
compiz-start
```

---

### Post by samssf on 2006-09-25
I'd suggest following the method in Ubuntu Guide. I tried a bunch of how-tos, but ultimately this is the one that got me running Xgl + compiz. Follow it exactly and see if it helps.

---

### Post by sarhento_lobo on 2006-09-25
> **samssf said:**
> I'd suggest following the method in Ubuntu Guide. I tried a bunch of how-tos, but ultimately this is the one that got me running Xgl + compiz. Follow it exactly and see if it helps.

dude, you forgot the link.

---

### Post by n00b@linux on 2006-09-25
> **samssf said:**
> I'd suggest following the method in Ubuntu Guide. I tried a bunch of how-tos, but ultimately this is the one that got me running Xgl + compiz. Follow it exactly and see if it helps.
I did.  It's not the guidance I'm having a problem with, it's getting a hold of the packages I need!

---

### Post by cmost on 2006-09-25
If you guys want Quinnstorm's version of Compiz (a.k.a. Beryl) you're going to have to wait until she and her band of devs completes the transition to the new fork.  The packages were removed to fix bugs and rebadge (at least according to the ruminations on the compiz forums.)  You can still run vanilla compiz (the version devised and maintained by Novell developers.)

---

### Post by n00b@linux on 2006-09-26
Where do I get the compiz vanilla packages (and instructions)?

---

### Post by Pugaciov on 2006-09-27
> **Dinerty said:**
> [http://www.compiz.net/topic-4690-2.html](http://www.compiz.net/topic-4690-2.html)

Check post #17 for the downloads mate;)

I tried to install the cgwd deb but it says that I already have a cgwd package installed. The CGWD Themer icon does appear, but it doesn't work...

---

### Post by Dinerty on 2006-09-27
> **Pugaciov said:**
> I tried to install the cgwd deb but it says that I already have a cgwd package installed. The CGWD Themer icon does appear, but it doesn't work...

Do you recieve any erros while trying to open it?. What happens if you run it from terminal?

---

### Post by Pugaciov on 2006-09-28
> **Dinerty said:**
> Do you recieve any erros while trying to open it?. What happens if you run it from terminal?

I receive that error when GDebi tries to install it.
What do you mean with run it from the terminal? Do you mean with dpkg?

---

