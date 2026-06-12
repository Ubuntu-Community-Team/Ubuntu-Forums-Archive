---
title: "Fonts and Mouse Pointers"
date: 2005-05-10
forum: Desktop Environments
---

### Post by Chromance on 2005-05-10
I have a 15.4 wide screen which displays 1600 by 1050. 
Yah things look a little small ,but ive managed to tweak
it to a decent size.  Problem is I don't like the fonts. I 
want MS windows type fonts in my linux !! can't seem
to make it work that way though. As well I need some help
With my mouse pointer size! its way too small anyone know
how to make it larger?

Chromance

---

### Post by Xerampelinae on 2005-05-10
You can install ms fonts

apt-get install msttfonts

and maybe you could change to a bigger cursor... here's a howto for gentoo, but it should apply to ubuntu too

[http://forums.gentoo.org/viewtopic-t-47057-highlight-cursor.html](http://forums.gentoo.org/viewtopic-t-47057-highlight-cursor.html)

---

### Post by RastaMahata on 2005-05-10
[QUOTE=Chromance]I have a 15.4 wide screen which displays 1600 by 1050. 
Yah things look a little small ,but ive managed to tweak
it to a decent size.  Problem is I don't like the fonts. I 
want MS windows type fonts in my linux !! can't seem
to make it work that way though. As well I need some help
With my mouse pointer size! its way too small anyone know
how to make it larger?

Chromance[/QUOTE]
 Please do not ask questions in this forum :(

---

### Post by bored2k on 2005-05-10
[QUOTE=Xerampelinae]You can install ms fonts

apt-get install msttfonts

and maybe you could change to a bigger cursor... here's a howto for gentoo, but it should apply to ubuntu too

[http://forums.gentoo.org/viewtopic-t-47057-highlight-cursor.html](http://forums.gentoo.org/viewtopic-t-47057-highlight-cursor.html)[/QUOTE]
 Isnt it sudo apt-get install msttcorefonts?
And for the cursor, just install gcursor and run it.

---

### Post by Xerampelinae on 2005-05-10
[QUOTE=bored2k]Isnt it sudo apt-get install msttcorefonts?
And for the cursor, just install gcursor and run it.[/QUOTE]
 You're right.  My bad memory. :\

---

### Post by Chromance on 2005-05-10
Ok I tried Gcursor and ran the program , and selected a new cursor theme
and nothing has changed ! same small dinky pointer arrrow.

---

### Post by ow50 on 2005-05-10
[QUOTE=Chromance]Ok I tried Gcursor and ran the program , and selected a new cursor theme
and nothing has changed ! same small dinky pointer arrrow.[/QUOTE]

You need log out and log back in to see the changes. Also note that all cursor themes don't support the size adjustment.

---

### Post by Segovia on 2005-05-10
[QUOTE=RastaMahata]Please do not ask questions in this forum :([/QUOTE]
Eh?

---

### Post by Xerampelinae on 2005-05-10
[QUOTE=Segovia]Eh?[/QUOTE]
 It was originally posted in tips and tricks

---

### Post by Segovia on 2005-05-10
[QUOTE=Xerampelinae]It was originally posted in tips and tricks[/QUOTE]
Ah, gotcha.

---

### Post by davidmigl on 2005-05-11
[QUOTE=bored2k]Isnt it sudo apt-get install msttcorefonts?
And for the cursor, just install gcursor and run it.[/QUOTE]
 This is what I get when I try to install the mscore fonts.

```
dennymigl@Hp:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
```

Has it been able to work for you?  Anyone have any ideas what I can do to get it working??

---

### Post by Xerampelinae on 2005-05-11
You probably have to add an extra repository to the file /etc/apt/sources.list

I'm not sure which one, but I suspect it would be the backports.  Below is my complete file, which you could copy, or perhaps you only need to add the last two lines (backports).

After changing this file, be sure to run "sudo apt-get update"

```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

#deb ftp://ftp.nerim.net/debian-marillat stable main
#deb ftp://ftp.nerim.net/debian-marillat unstable main
#deb ftp://ftp.nerim.net/debian-marillat testing main
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

---

