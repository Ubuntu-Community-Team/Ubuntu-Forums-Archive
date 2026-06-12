---
title: "Installing beryl"
date: 2007-03-08
forum: Desktop Environments
---

### Post by progrockusa on 2007-03-08
Ok i'm at the 
sudo apt-get install nvidia-glx
and it's coming down REALLY slow. does anyone know another place i can get the 2 linux-restricted-modules-2.6.17-10-386  says it's going to take 15 hours O.O

---

### Post by Bachstelze on 2007-03-08
1) Your system is not up to date, the latest kernel is 2.6.17-11.

2) You should use the generic kernel, not the 386.

3) Please paste your /etc/apt/sources.list.

---

### Post by progrockusa on 2007-03-08
> **HymnToLife said:**
> 1) Your system is not up to date, the latest kernel is 2.6.17-11.

2) You should use the generic kernel, not the 386.

3) Please paste your /etc/apt/sources.list.

hmmm it should be up to date
remember i'm a noob i don't know where to get that list

---

### Post by Bachstelze on 2007-03-08
```
gksudo gedit /etc/apt/sources.list
```

It will prompt for your password and open the file in the gedit text editor. Then you can copy/paste it here.

---

### Post by taurus on 2007-03-08
Or why not just use

```
cat /etc/apt/sources.list
```
Then, there is no password required.

---

### Post by progrockusa on 2007-03-08
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable

well it doesn't bother me that it's out of date a bit only need to get 20 megs.. the problem is i'm only getting like 300b/s  so it'll take like 15 hours... can i get these updates anywhere else?

---

### Post by Bachstelze on 2007-03-08
Because the file is rather long in Ubuntu, so if I just *cat* it, I need to resize the terminal window to have it entirely on the screen so I can paste it, which I don't find convenient :)

@progrockusa, maybe it's just [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) having problems. Try removing the us in all such lines so it gives you [http://archive.ubuntu.com](http://archive.ubuntu.com)

Then save the file, do

```
sudo apt-get update
sudo apt-get install linux-generic
sudo apt-get dist-upgrade
```

then reboot and show us what *uname -r* says.

---

### Post by taurus on 2007-03-08
But if you are using gnome-terminal, then there should be a scroll bar where you can scroll up unless you turn it off.  In fact, there is a scroll bar for aterm, eterm, rxvt, rxvt-unicode, Terminal, etc.

---

### Post by progrockusa on 2007-03-08
stable/linux-restricted-modules-2.6.17-10-generic_2.6.17.7-10.1-9746_i386.deb 
this file is coming down slower than snail mail

---

### Post by Bachstelze on 2007-03-08
I'm using Konsole and there is a scrollbar too, actually it's because I don't use real copy/paste but the shortcut with the mouse middle button, so if not all the text is visible on the screen, not all of it will be pasted.

@progrockusa, edit for you in my previous post :)

---

### Post by progrockusa on 2007-03-08
i need linux-restricted-modules-2.6.17.10-generic
linux-restricted-modules-2.6.17.11-generic
and nvidia-glx
for some reason these updates are coming down at less than 1 kbps do you guys know where i can get these updates from elsewhere?

---

### Post by Bachstelze on 2007-03-08
I was under the impression that I suggested you tried anothe mirror for apt. When you ask for help, it's better to actually read the answers you're given ;)

---

### Post by progrockusa on 2007-03-08
?

---

### Post by Bachstelze on 2007-03-08
There :

> **HymnToLife said:**
> @progrockusa, maybe it's just [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) having problems. Try removing the us in all such lines so it gives you [http://archive.ubuntu.com](http://archive.ubuntu.com)

Then save the file, do

```
sudo apt-get update
sudo apt-get install linux-generic
sudo apt-get dist-upgrade
```

then reboot and show us what *uname -r* says.

---

### Post by progrockusa on 2007-03-08
thanks 
well i'm not sure why i need the updates i went ahead and installed beryl
all i can say is WOW  vista is lame in comparison very very nice. i'll try to get these updates anyhow

BTW  [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) this website is just very very slow which is where my updates are coming from. i guess i'll just leave it up overnight

---

### Post by progrockusa on 2007-03-08
grrr... i messed with the setting for blur effects now beryl just freezes each time i start it up. what do i do?

---

### Post by K.Mandla on 2007-03-08
(Moved to Desktop Environments. ;) )

---

### Post by progrockusa on 2007-03-08
i mean is their a way i can disable the blur effects from a config file?

---

