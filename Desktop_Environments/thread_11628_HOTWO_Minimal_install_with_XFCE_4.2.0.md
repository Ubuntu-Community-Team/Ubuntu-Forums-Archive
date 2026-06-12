---
title: "HOTWO: Minimal install with XFCE 4.2.0"
date: 2005-01-18
forum: Desktop Environments
---

### Post by frontline3k on 2005-01-18
Hi.
I have an old computer (IBM Pentium 200 MMX with 64 MB and a 2 GB HDD) and I want a minimal install with XFCE 4.2.0 (from [http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)) , something like [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) but with XFCE 4.2.0 instead of IceWM.
Anyone knows how to do it step-by-step ?

I'm tired of dependencies check.
I tried with XFCE installer and ... always wants a new dependecies (Glib, Gtk 2.0 and so on).

Thanks a lot.

---

### Post by fabinho on 2005-01-18
[QUOTE=frontline3k]Hi.
I have an old computer (IBM Pentium 200 MMX with 64 MB and a 2 GB HDD) and I want a minimal install with XFCE 4.2.0 (from [http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)) , something like [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) but with XFCE 4.2.0 instead of IceWM.
Anyone knows how to do it step-by-step ?

I'm tired of dependencies check.
I tried with XFCE installer and ... always wants a new dependecies (Glib, Gtk 2.0 and so on).

Thanks a lot.[/QUOTE]

1) Have you ever tried BeatrIX, [http://www.watsky.net/](http://www.watsky.net/) ? It is ubuntu based, uses gnome and is made to run on old machines. The ISO has less than 200 MB;

2) The best way to install Xfce is using the oscilation repositores (you have to change the /etc/apt/souces.list file). Instructions are [here](http://www.os-works.com/view/debian/) .

---

### Post by frontline3k on 2005-01-18
> 2) The best way to install Xfce is using the oscilation repositores (you have to change the /etc/apt/souces.list file). Instructions are here .
I am using oscilation repositores, and still not working  :sad: 

I'll try BeatrIX, but I still like Ubuntu  :D 

Looking forward for other ideeas.

---

### Post by frontline3k on 2005-01-19
Maybe this will help. Here are the messages after apt-get install xfce4

```
Reading Package Lists...
Building Dependency Tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xfce4: Depends: xfce4-session (>= 4.2.0) but it is not going to be installed
         Depends: xfce4-utils (>= 4.2.0) but it is not going to be installed
         Depends: xfdesktop4 (>= 4.3.6.3-1) but it is not going to be installed
         Depends: xfce4-cpugraph-plugin (>= 0.2.2.xfld-1) but it is not going to be installed
```

And /etc/apt/sources.list
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu warty main restricted
# deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu warty universe
# deb-src http://archive.ubuntu.com/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
# deb-src http://security.ubuntu.com/ubuntu warty-security main restricted

# XFCE
deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main

# Ubuntu backports
deb http://ubuntu-bp.sourceforge.net/ubuntu warty-backports main universe
 
```

Any help is apreciated. Thanks.

---

### Post by Michael on 2005-01-22
Oh god knows I've been through there.. can't manage to install any newer XFCE version other than the old 4.0 one in the universe repository.

XFCE 4.2 for debian/ubuntu = dependency hell!!!

A HOWTO for Ubuntu+XFCE will nice, I hope someone will do it one day :)

---

