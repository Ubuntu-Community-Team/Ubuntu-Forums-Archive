---
title: "Help me with KDM Theme Manager"
date: 2005-04-18
forum: Desktop Environments
---

### Post by Cool_dude_Prav on 2005-04-18
Help me plz!!! ](*,)  ](*,) 

I tried to install KDM Theme Manager from [www.kde-look.org](www.kde-look.org) and hence i downloaded the .deb and installed using dpkg -i <kdm-file-name>.deb

I get the following error!!!

```
praveen@Pravnet:~$ sudo dpkg -i kdmtheme_0.8.2-1_i386.deb
(Reading database ... 74356 files and directories currently installed.)
Preparing to replace kdmtheme 0.8.2-1 (using kdmtheme_0.8.2-1_i386.deb) ...
Unpacking replacement kdmtheme ...
dpkg: dependency problems prevent configuration of kdmtheme:
 kdmtheme depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 kdmtheme depends on libidn11 (>= 0.5.13); however:
  Version of libidn11 on system is 0.5.2-3.
dpkg: error processing kdmtheme (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdmtheme

```

Even though my libs are the latest, it refuses to configure..

plz help me!!!  :confused:

---

### Post by TravisNewman on 2005-04-18
[QUOTE=Cool_dude_Prav]Help me plz!!! ](*,)  ](*,) 

I tried to install KDM Theme Manager from [www.kde-look.org](www.kde-look.org) and hence i downloaded the .deb and installed using dpkg -i <kdm-file-name>.deb

I get the following error!!!

```
praveen@Pravnet:~$ sudo dpkg -i kdmtheme_0.8.2-1_i386.deb
(Reading database ... 74356 files and directories currently installed.)
Preparing to replace kdmtheme 0.8.2-1 (using kdmtheme_0.8.2-1_i386.deb) ...
Unpacking replacement kdmtheme ...
dpkg: dependency problems prevent configuration of kdmtheme:
 kdmtheme depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 kdmtheme depends on libidn11 (>= 0.5.13); however:
  Version of libidn11 on system is 0.5.2-3.
dpkg: error processing kdmtheme (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdmtheme

```

Even though my libs are the latest, it refuses to configure..

plz help me!!!  :confused:[/QUOTE]
 It says there that, for example, libfontconfig1 is at version 2.2.3-etc., but it needs 2.3.0. The latest versions of these dependencies in the ubuntu repositories aren't high enough for kdmtheme 0.8.2-1 to work. The easiest way to go would be to download an older build of kdmtheme.

---

### Post by Cool_dude_Prav on 2005-04-18
[QUOTE=panickedthumb]It says there that, for example, libfontconfig1 is at version 2.2.3-etc., but it needs 2.3.0. The latest versions of these dependencies in the ubuntu repositories aren't high enough for kdmtheme 0.8.2-1 to work. The easiest way to go would be to download an older build of kdmtheme.[/QUOTE]
 Is there any way by which i can install the latest libs... Maybe from elsewhere???

Plz reply ASAP...

---

### Post by TravisNewman on 2005-04-18
Yes, you can find a repo that has them using apt-get.org, but that's risky. Seriously, your best bet is using an older version of kdmtheme that will work with what you already have.

---

### Post by Cool_dude_Prav on 2005-04-18
[QUOTE=panickedthumb]Yes, you can find a repo that has them using apt-get.org, but that's risky. Seriously, your best bet is using an older version of kdmtheme that will work with what you already have.[/QUOTE]
 I cant even google out older versions!!! Or maybe I dont know to google :(

Plz help me...

Will me sys crash if I try installing the lib manually???
:arrow: If no, plz post here on how to do it..
:arrow: If yes, plz post me an older version's link :D

---

### Post by TravisNewman on 2005-04-18
There is no simple answer. The only way to find out is to do it. I don't suggest that, but its your choice, and I did tell you how to do it. apt-get.org has a searchable database of packages. When you find a repo that has the libs, put that repo in your /etc/apt/sources.list

if you don't want to go through all that hassle, I'd suggest going to the site you got the kdmtheme manager and looking for an old version there, and if it's not there ask someone there where to find it.

But I'm not going to search google for you to find an older version, and I'm not going to go through step by step on how to update those libs, because it would pretty much require me to do it all to find out. I've given you the tools. If you get stuck, feel free to ask questions about it, but specific questions.

---

### Post by Cool_dude_Prav on 2005-04-18
[QUOTE=panickedthumb]There is no simple answer. The only way to find out is to do it. I don't suggest that, but its your choice, and I did tell you how to do it. apt-get.org has a searchable database of packages. When you find a repo that has the libs, put that repo in your /etc/apt/sources.list

if you don't want to go through all that hassle, I'd suggest going to the site you got the kdmtheme manager and looking for an old version there, and if it's not there ask someone there where to find it.

But I'm not going to search google for you to find an older version, and I'm not going to go through step by step on how to update those libs, because it would pretty much require me to do it all to find out. I've given you the tools. If you get stuck, feel free to ask questions about it, but specific questions.[/QUOTE]
 Hehe... Your post seems more of a Disclaimer than a suggestion :lol:
LOL Kidding...

BTW thnx mate!!!

Shall try and tell if successful...

---

### Post by Cool_dude_Prav on 2005-04-18
Hey!!!

I found only the same version as I have there. 2.3 version is not yet there!!! :sad:

Hey Mr.PanickedThumb, plz help me!!!

---

### Post by Cool_dude_Prav on 2005-04-18
Someone plz help me reg the libfontconfig1 as the latest version is unavailable...

PLz..

---

### Post by Cool_dude_Prav on 2005-04-21
BUMP..

Sorry but had to bump, as no satisfactory answers yet...

Plz temme atleast on where to get older versions... :(

---

