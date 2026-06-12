---
title: "Graphical login"
date: 2005-08-20
forum: Desktop Environments
---

### Post by myha on 2005-08-20
Hi!

Im having a little problem with system login... I cant get gnome to start in graphic mode, when i boot up i always have text login, and i have to startx to start gnome...

Can anyone tell me how to change this to graphical login?

Thanks in advance,
Miha

---

### Post by amastronardi on 2005-08-20
Install Gnome Display Manager

```
apt-get install gdm
```

If it is already installed, try:

```
pkg-reconfigure gdm
```

Cheers, Adrian.

---

### Post by amastronardi on 2005-08-20
[QUOTE=amastronardi]If it is already installed, try:

```
pkg-reconfigure gdm
```[/QUOTE]

It should say:

```
dpkg-reconfigure gdm
```

Sorry for the typo,

Adrian

---

### Post by rejser on 2005-08-20
[QUOTE=myha]Hi!

Im having a little problem with system login... I cant get gnome to start in graphic mode, when i boot up i always have text login, and i have to startx to start gnome...

Can anyone tell me how to change this to graphical login?

Thanks in advance,
Miha[/QUOTE]
 hmmm... in your /etc/inittab which runlevel is set?
defaults runlevel ??

---

### Post by myha on 2005-08-20
[QUOTE=rejser]hmmm... in your /etc/inittab which runlevel is set?
defaults runlevel ??[/QUOTE]
 Well...

# The default runlevel.
id:2:initdefault:

When i try to run dpkg-reconfigure gdm I get the following error:

/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed

I tried to update it but i don't have installcd here so i'll have to try it on monday i guess...
Here is the output:

Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  gdm
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.

If I install this will it work? How come the gnome is working if i startx if it doesnt have this package?

Thank you both!
Regards, Miha

---

### Post by dbeckham32 on 2005-08-20
Same thing happened to me. Try typing this into a terminal session:

sudo dpkg-reconfigure gdm

---

