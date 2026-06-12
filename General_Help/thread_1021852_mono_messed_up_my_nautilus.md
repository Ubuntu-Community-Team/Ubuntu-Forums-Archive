---
title: "mono messed up my nautilus"
date: 2008-12-26
forum: General Help
---

### Post by Unlearned on 2008-12-26
ok i found a old thread here, but i need more help

i installed some version of mono yesterday. this morning ubuntu worked, but tonight it gives the error message: bonobo-activation
server (error code:3)

i tried to find where the new mono had installed, but could not find it. i found one finally, but could not get unistall to work....doh

i only way to get gnome to work right is to enter failsafe mode

can anyone give me the idiot's guide to fixing this. pretend you are telling someone who has never looked at a computer...then dumb it down :)

---

### Post by directhex on 2008-12-26
Where did this "some version of mono" come from?

---

### Post by northern lights on 2008-12-26
> **directhex said:**
> Where did this "some version of mono" come from?
This would indeed be helpful info.

If you installed from the repositories (Add/Remove dialog / gnome-app-install, Synaptic, apt-get or aptitude), you could run```
sudo aptitude purge mono-common
```to get rid of it and possibly reinstall it.

Further, there might be broken references in your *~./bashrc* file to mono in the *PATH* section. Check whether you can remove those.

---

### Post by Unlearned on 2008-12-26
was trying to get a program to work and found this on its forum:

downloaded from:
[http://ftp.novell.com/pub/mono/archive/1.2.6/download/](http://ftp.novell.com/pub/mono/archive/1.2.6/download/)

then...

chmod a+x mono-1.2.6_6-installer.bin
sudo ./mono-1.2.6_6-installer.bin

then it said.....
Need to install gmcs with the command in terminal
sudo apt-get install mono-gmcs

---

### Post by northern lights on 2008-12-26
mkey. Since you installed from neither the repositories nor a .deb (binary installer / shell script), removing via aptitude or apt-get will not work.

You have to figure out where it installed to, to do so, run```
locate mono
``` and find the directory it got installed. Subsequently run```
sudo rm -rf /path/to/mono/
``` where the path needs to be replaced by what you found. Could for instance be /usr/bin/mono/, not too sure.

Have you tried checking ~./bashrc for mono entries in the PATH section?

---

### Post by directhex on 2008-12-26
o_o

Some people are clearly on a crusade to mess up their systems

Firstly, Ubuntu comes with Mono installed by default, so your starting position is with the system Mono. Next, you've overridden it with a non-Ubuntu, obsolete i386-only installer. Finally, you've installed the system version of the compiler.

There is no possible way to know what a mess you've made of your system at this point. It's not Mono's fault, it's yours.

---

### Post by northern lights on 2008-12-26
> **directhex said:**
> Some people are clearly on a crusade to mess up their systems...
I know man. I don't see why anybody'd do this.

@the OP: The Ubuntu native mono does reside in /usr/bin/mono/

So your best chances to recover probably are running```
sudo rm -rf /usr/bin/mono/ && sudo rm -rf /usr/share/mono-1.0/
```
and subsequently```
sudo aptitude purge mono-common && sudo apt-get autoclean && sudo apt-get autoremove
```then```
sudo rm -rf /var/lib/dpkg/info/mono*
```and at last```
sudo apt-get update && sudo apt-get install mono-common
```

If this fails, I'd opt for a reinstall.

directhex is absolutely right, though. Next time, be aware of what you install...

---

### Post by Unlearned on 2008-12-26
lot of truth there :)

note to self: never blindly follow instructions you have not verified in some way

---

