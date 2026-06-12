---
title: "Native Online Poker Program?"
date: 2007-07-19
forum: Gaming &amp; Leisure
---

### Post by Majorix on 2007-07-19
So what are the native clients for online poker on Linux? I know that its possible to run some programs through Wine, but there are always small problems when using Wine of course.

So I am settled looking for a native online poker client for Ubuntu. I don't care if you have to compile it from source etc, it is just that it should be popular and nice looking.

Thanks a lot.

---

### Post by Ripfox on 2007-07-19
Bump

---

### Post by hikaricore on 2007-07-19
[http://www.pok3d.com/](http://www.pok3d.com/)  ^_^

I've never tried it, but I've heard good things about it.

They even have a repo for dapper/edgy listed here: [http://www.pok3d.com/download.php](http://www.pok3d.com/download.php)
(should work for feisty barring any strange complications)

---

### Post by Nythain on 2007-07-19
looks kinda sweet, downloading now... ill let you know what i think after i play a bit

---

### Post by Majorix on 2007-07-20
> **hikaricore said:**
> [http://www.pok3d.com/](http://www.pok3d.com/)  ^_^

I've never tried it, but I've heard good things about it.

They even have a repo for dapper/edgy listed here: [http://www.pok3d.com/download.php](http://www.pok3d.com/download.php)
(should work for feisty barring any strange complications)

OK thanks but on the download page there is only Dapper and Edgy? No Feisty...

---

### Post by Nythain on 2007-07-20
i went ahead and added teh edgy repo and installed from there with no problems, and it runs so i guess it works

---

### Post by hikaricore on 2007-07-20
> **hikaricore said:**
> 
They even have a repo for dapper/edgy listed here: [http://www.pok3d.com/download.php](http://www.pok3d.com/download.php)
_**(should work for feisty barring any strange complications)**_

> **Majorix said:**
> OK thanks but on the download page there is only Dapper and Edgy? No Feisty...

:p

---

### Post by Majorix on 2007-07-20
Ok sorry I just wanted to ask if there was a feisty version :) Guess I will add the edgy repo then.

Thanks.

---

### Post by hikaricore on 2007-07-20
If there were a feisty version, there would honestly be _no_ difference, except maybe the dependancy version numbers.

All of the data would be exactly the same.  ^_^

---

### Post by Majorix on 2007-07-20
Ok when I tried to install this, I got the following errors in the command line:
```
sudo aptitude install python-poker3d poker3d-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libopenscenegraph4 
The following NEW packages will be automatically installed:
  apg dbconfig-common libalut0 libcal3d11c2a libcoin40c2 libopenalpp-cvs1 
  libopenthreads4 libosgal-cvs1 libosgcal0 libpoker-eval libpoker3d 
  libproducer4 python-crypto python-libxslt1 python-mysqldb python-pam 
  python-poker-engine python-poker-network python-poker2d python-pygame 
  python-pyopenssl python-pypoker-eval python-serial python-simplejson 
  python-soappy python-twisted python-twisted-bin python-twisted-conch 
  python-twisted-core python-twisted-lore python-twisted-mail 
  python-twisted-names python-twisted-news python-twisted-runner 
  python-twisted-web python-twisted-words python-zopeinterface xwnc 
The following NEW packages will be installed:
  apg dbconfig-common libalut0 libcal3d11c2a libcoin40c2 libopenalpp-cvs1 
  libopenthreads4 libosgal-cvs1 libosgcal0 libpoker-eval libpoker3d 
  libproducer4 poker3d-data python-crypto python-libxslt1 python-mysqldb 
  python-pam python-poker-engine python-poker-network python-poker2d 
  python-poker3d python-pygame python-pyopenssl python-pypoker-eval 
  python-serial python-simplejson python-soappy python-twisted 
  python-twisted-bin python-twisted-conch python-twisted-core 
  python-twisted-lore python-twisted-mail python-twisted-names 
  python-twisted-news python-twisted-runner python-twisted-web 
  python-twisted-words python-zopeinterface xwnc 
0 packages upgraded, 41 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.6MB of archives. After unpacking 122MB will be used.
The following packages have unmet dependencies:
  libopenscenegraph4: Depends: libgdal1-1.3.1 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libcfitsio2 [2.510-1.3 (feisty, feisty)]
libgdal1-1.3.2 [1.3.2-2ubuntu1 (feisty, feisty)]
libgeos2c2a [2.2.3-3 (feisty, feisty)]
libhdf4g [4.1r4-18.1ubuntu1 (feisty, feisty)]
libnetcdf3 [3.6.1-0.1build1 (feisty, feisty)]
libopenscenegraph4 [1.2.0-2build1 (feisty, feisty)]
proj [4.4.9d-2 (feisty, feisty)]

Score is -398

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

Why does it want to install so many packages?

Is there a way to fix this? :confused:

---

### Post by hikaricore on 2007-07-20
Errmmm... just allow it to install the needed packages?
Unless it's downgrading or removing something it's fine.

The game obviously has many dependancies which is not uncommon.

---

### Post by Majorix on 2007-07-20
OK I let it run and it did the job. Ubuntu was complaining it could be insecure and stuff that is why I acted slowly :)

poker3d doesn't work on my machine, I guess thanks to my old and incompatible video card. I will maybe one day try this on a faster pc.

---

### Post by el_itur on 2007-07-20
have you tried pok3d? I've noticed that there is a package named poker3d and it looks just like it, even the description is the same, but it is not :P

---

### Post by hikaricore on 2007-07-20
> **el_itur said:**
> have you tried pok3d? I've noticed that there is a package named poker3d and it looks just like it, even the description is the same, but it is not :P

I believe we were talking about pok3d the entire time.  O.o

---

### Post by el_itur on 2007-07-20
> **Majorix said:**
> 

[SIZE="3"]poker3d[/SIZE] doesn't work on my machine, I guess thanks to my old and incompatible video card. I will maybe one day try this on a faster pc.

> **hikaricore said:**
> I believe we were talking about pok3d the entire time.  O.o

I believe he is talking about poker3d, I've just see that package next to pok3d when I was trying to install it so I think it worth to clarify. But may be I'm wrong.

---

### Post by Nythain on 2007-07-21
it was pok3d that he tried installing, i know because i just installed it last night and had the exact  same set of dependencies... runs great on my machine.

i was reading thier forums aparently there's a pok2d for lower end machines, you might want to research into that if you are having trouble running pok3d

---

### Post by Majorix on 2007-07-21
Yeah I tried poker2d and there were a few problems with the graphics. At some parts it was transparent, the buttons were unclickable etc.

Guess I will just stick with Wine and the windows poker games :(

---

### Post by Nythain on 2007-07-23
ok, so after days of playing this game, im totally freaking hooked... i love it... its like poker, with 3d people, that makes me happy.

only two complaints
A. Not a big enough player base... middle of the night and there is no one on... most i've seen during peak daytime hours is like 20 something

B. Everyone is flippin french... like EVERYONE... i googled to see if maybe i was on a wrong server, or if there were regional servers at all, and i only found the one server... and they are ALL french... i cant comunicate with anyone... wich kinda sucks since we're all really cool 3d avatars

overall... i give this game an 8/10

---

### Post by UbuWu on 2007-07-24
You might want to watch [PokerTH]("http://www.pokerth.net/"). It doesn't support online games yet, but it is planned and it is developed at a fast pace.

---

### Post by Nythain on 2007-07-24
yeah, i played pokerth... it was ok, but without online play it got boring real fast

---

### Post by janne_oksanen on 2007-10-06
Simba Poker has a nice native poker client. It's a fairly new contender in field and the player base is not very big. But who knows? It might pick up soon.

---

