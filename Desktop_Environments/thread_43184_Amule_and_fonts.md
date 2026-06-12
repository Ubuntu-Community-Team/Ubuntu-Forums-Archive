---
title: "Amule and fonts"
date: 2005-06-21
forum: Desktop Environments
---

### Post by frs-design on 2005-06-21
Hi all !

I'd like amule to be smaller on my screen: i have big fonts, and all is big in fact  :???: 

Is there a way to change it or to use the qt themes like with the gtk apps ?

Thank you !

++

---

### Post by Zeddicus on 2005-06-22
Actually, amule isn't a qt app -- it's a gtk(1) app. :p

As for changing the fonts... you could install a gtk1 theme changer (gtk-theme-switch), but even then, the fonts wouldn't be anti-aliased.

However -- new (read: post 2.0) builds of Amule supposedly use GTK2.  Installing that should solve your problem.

According to [http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian](http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian)

Adding:

```
 deb http://www.vollstreckernet.de/debian/ testing amule
 deb http://www.vollstreckernet.de/debian/ testing wx
```

to /etc/apt/sources.list, then doing a:

```

Now run apt-get update && apt-get install amule
```

Should get you a much prettier amule. :)

[size=+1][color=Red]Big Honking Warning![/color][/size]:  I haven't done this myself, so for all I know, your computer will explode.  That said, I doubt that'd happen. ;)

---

### Post by frs-design on 2005-06-23
Thank you for this reply but it didn't change anything ... :-|

---

### Post by triplehelix on 2005-07-03
I have a similar problem with a few applications having big ugly fonts, not like the rest of the apps. Mplayer menu fonts, xmms menu fonts, and the whole amule layout. I've fiddle with it a little, but I seriously don't want to hose up my box here.  ](*,)

---

### Post by ign on 2005-07-29
i have the same problem. i read somewhere in the forum that the solution was to install gtk2, but it didn't change anything...
does anyone knows how to correct this?

---

### Post by Feanor on 2005-07-29
try to use amule 2.0.3, I've  normal fonts on this version...

I take it from some repository, I don't know exactly where... Here is my sources.list

```
#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://it.archive.ubuntu.com/ubuntu hoary main restricted
 deb-src http://it.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://it.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://it.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://it.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://it.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

 deb http://archive.ubuntu.com/ubuntu hoary multiverse
 deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

# deb ftp://ftp.nerim.net/debian-marillat stable main
# deb ftp://ftp.nerim.net/debian-marillat unstable main
# deb ftp://ftp.nerim.net/debian-marillat testing main

# repository da cui ho preso java sdk2
# deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

 deb http://ubuntu.tower-net.de/ubuntu/ hoary java

# Ubuntu backports -> aggiornamento versioni dei pacchetti

# deb http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
# deb http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted

 deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
 deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted


## Backports

  deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
  deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
  deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
  deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

## Kubuntu
  
  deb http://kubuntu.org/hoary-kde341 hoary-updates main
  deb http://kubuntu.org/hoary-koffice14 hoary-updates main
  # deb http://download.kde.org/stable/3.4.1/kubuntu hoary-updates main

## Altre repository per Kubuntu
## applicazioni non supportate dalle repositories ufficiali

  deb http://dinton.no-ip.org/ kubuntu main
  deb-src http://dinton.no-ip.org/ kubuntu main
```

---

### Post by Jeltje on 2005-08-06
Same here. I now use aMule 2.0.3 from the [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)  repositories. No more big fonts etc.

---

### Post by samwyse on 2005-08-06
add a .gtkrc.mine file in home directory:

```
style "user-font"
{
fontset="-adobe-helvetica-medium-r-normal-*-12-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"

```

---

### Post by buldir on 2005-08-27
[QUOTE=samwyse]add a .gtkrc.mine file in home directory:

```
style "user-font"
{
fontset="-adobe-helvetica-medium-r-normal-*-12-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"

```[/QUOTE]

samwyse...you rock.  xmms and mplayer menus look smashing now.

---

### Post by starscalling on 2006-09-12
> **samwyse said:**
> add a .gtkrc.mine file in home directory:

```
style "user-font"
{
fontset="-adobe-helvetica-medium-r-normal-*-12-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"

```

yeah that fixed it
though the file its in is .gtkrc-1.2-gnome2
which talks about including .gtkrc.mine or something
but i just tossed it in the main one
ive got enough crap in my home dir
;d
but anyay thanx

---

