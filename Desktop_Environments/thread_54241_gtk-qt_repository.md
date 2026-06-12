---
title: "gtk-qt repository"
date: 2005-08-04
forum: Desktop Environments
---

### Post by gingermark on 2005-08-04
Hiya,

I've just done a clean install of Kubuntu Hoary because overall I prefer KDE, but there are still some GNOME programs I prefer. Obviously I can run them but they look a little out of place.

I read on the KDE website there was a theme that would make these programs seem more at home within the KDE. I followed the instructions on the site, and the theme appeared to have installed, but there was no entry in the Control Centre.

I then came and had a look here. There seem to be several references to the theme, and instructions to apt-get it, but when I tried apt-get couldn't find it, and I can't find any references to which repository it is in.

I've added all the repositories listed in the Unofficial Guide, and can't seem to find where it might be searching these forums or the rest of the net.

Apologies if I've missed something obvious, but if anyone could help it would be most appreciated.

Many thanks,
gingermark.

---

### Post by drizek on 2005-08-04
[QUOTE=gingermark]Hiya,

I've just done a clean install of Kubuntu Hoary because overall I prefer KDE, but there are still some GNOME programs I prefer. Obviously I can run them but they look a little out of place.

I read on the KDE website there was a theme that would make these programs seem more at home within the KDE. I followed the instructions on the site, and the theme appeared to have installed, but there was no entry in the Control Centre.

I then came and had a look here. There seem to be several references to the theme, and instructions to apt-get it, but when I tried apt-get couldn't find it, and I can't find any references to which repository it is in.

I've added all the repositories listed in the Unofficial Guide, and can't seem to find where it might be searching these forums or the rest of the net.

Apologies if I've missed something obvious, but if anyone could help it would be most appreciated.

Many thanks,
gingermark.[/QUOTE]
 (if youve installed it correctly)

kcontrol-appearance-gtk/qt theme engine-set it to use our kde styles and fonts.

---

### Post by gingermark on 2005-08-04
So, do I have to download either the source code or autopackage binary from [http://www.freedesktop.org/Software/gtk-qt](http://www.freedesktop.org/Software/gtk-qt) ?

I was hoping I could just install it via apt-get (as per the repository question)

Is installing from the source better than installing via the autopackage? I've never compiled anything from source before, but I have the software to do it, so I could always give it a go.

Thanks.

EDIT: I notice there is a version for debian here: deb [ftp://ftp.ekhis.org/ekhis/](ftp://ftp.ekhis.org/ekhis/) staging main

I know that as a rule it's a bad idea to install debian packages, but in this case is it likely to cause a problem?

---

### Post by drizek on 2005-08-04
[QUOTE=gingermark]So, do I have to download either the source code or autopackage binary from [http://www.freedesktop.org/Software/gtk-qt](http://www.freedesktop.org/Software/gtk-qt) ?

I was hoping I could just install it via apt-get (as per the repository question)

Is installing from the source better than installing via the autopackage? I've never compiled anything from source before, but I have the software to do it, so I could always give it a go.

Thanks.

EDIT: I notice there is a version for debian here: deb [ftp://ftp.ekhis.org/ekhis/](ftp://ftp.ekhis.org/ekhis/) staging main

I know that as a rule it's a bad idea to install debian packages, but in this case is it likely to cause a problem?[/QUOTE]
 id go with autopackage,

---

### Post by GeneralZod on 2005-08-04
Hi Mark,

I was simply able to install it via Synaptic, so it should be in one of the repositories listed in the Guide.  Can you post you /etc/apt/sources.list, please?  Maybe something's gotten lost, somwhere :)

---

### Post by gingermark on 2005-08-04
[QUOTE=GeneralZod]Hi Mark,

I was simply able to install it via Synaptic, so it should be in one of the repositories listed in the Guide.  Can you post you /etc/apt/sources.list, please?  Maybe something's gotten lost, somwhere :)[/QUOTE]

Thanks :-)

The sources.list file contatins the following:

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## XMMS-Scrobbler
deb [http://www.sommitrealweird.co.uk/ubuntu/](http://www.sommitrealweird.co.uk/ubuntu/) hoary scrobbler
deb-src [http://www.sommitrealweird.co.uk/ubuntu/](http://www.sommitrealweird.co.uk/ubuntu/) hoary scrobbler

---

### Post by gingermark on 2005-08-04
Sorry to "bump" this, as it were, but does anyone have have an idea on what repository I might be missing?

Many thanks.

---

### Post by GeneralZod on 2005-08-04
I'm not sure, so I'll post mine:
```

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


deb http://gb.archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu/ hoary main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://gb.archive.ubuntu.com/ubuntu/ hoary universe 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted 

deb http://security.ubuntu.com/ubuntu/ hoary-security universe 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe 


# deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted 
# deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted 

# deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted 
# deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted 

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted  
# deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted 
# deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted 

# deb ftp://ftp.nerim.net/debian-marillat/ unstable main  
# deb ftp://ftp.nerim.net/debian-marillat/ testing main 
# deb ftp://ftp.nerim.net/debian-marillat/ stable main  

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse 

# deb http://ubuntu.tower-net.de/ubuntu/ warty java 





# E17
deb http://ubuntu.nooms.de/ hoary/ 

#kde bluetooth
deb http://fred.hexbox.de/debian/ ./ 


deb-src http://kubuntu.org/hoary-kde342 hoary-updates main




```

---

### Post by samwyse on 2005-08-04
It's in the universe repository as "gtk2-engines-gtk-qt".

edit: gtk not qtk ](*,)

---

### Post by gingermark on 2005-08-05
[QUOTE=samwyse]It's in the universe repository as "gtk2-engines-qtk-qt".[/QUOTE]

Thanks. (It's actually "gtk2-engines-**g**tk-qt", but I'm sure that's what you meant!)

I blame the KDE site, as they kept saying it was called "gtk-qt", so that's what I was searching for. Grrr.

Thanks for everyone's help.

---

### Post by samwyse on 2005-08-05
[QUOTE=gingermark]Thanks. (It's actually "gtk2-engines-**g**tk-qt", but I'm sure that's what you meant!)[/QUOTE]
Yeah, that's what I meant :grin:

---

