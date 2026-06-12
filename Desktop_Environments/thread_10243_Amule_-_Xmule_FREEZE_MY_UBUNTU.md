---
title: "Amule - Xmule FREEZE MY UBUNTU"
date: 2005-01-06
forum: Desktop Environments
---

### Post by Sniffer on 2005-01-06
Hi Ubuntu fans,

After 2 months with a lot of changes in my ubuntu server :confused:  tryng to figure out WHY my system froze in a couple of moments or in a couple of hours, have changed my modem connection (For the NET) from USB to Ethernet, changed the kernel to K7 wich is more APPROPRIATE for my system, only installed stable packages, have taken out my USB bluetooth Dongle...but my problem persist...frozen system (wich i can only solve with my reset button, not to talk if any work is being done is LOST).


Finally i figure out what it is....amule and xmule packages....from hoary or the stable from warty just don't work......

Xmule open but when tryng to connect to any server close without reason or motive........either from hoary or warty.....

Amule works but after short or long time...is really a question of minutes or couple of hours just BLOCK / FREEZE whatever...... either packages from hoary and warty......

This conclusion comes when i left my computer for 2 days working without amule connected.....when i start amule it freeze in 1hour and a half.....

I don't know how to solve this one so my question, should i install amule from the source...the maitainers from ubuntu packages have any idea or heard about similar problems.....

Thanks
Sniff.

Update:even an memtest i have made but my OCZ RAM was fine....have changed the speed for 333 instead of 400 just looking for stability......no worthy

---

### Post by Sniffer on 2005-01-06
Here it goes the terminal result for xmule version 1.94b


OOPS! - Seems like xMule crashed
--== BACKTRACE FOLLOWS: ==--

Segmentation fault

---

### Post by ulrich on 2005-01-07
since the xmule-project is dead i would recommend to stick with amule.

do you fiddled with preferences in amule/xmule right after installtion?
there are many preferences that can kill your connection/system...
have you tried to start with a fresh install?

```

apt-get --purge amule

```
purge kicks everything regarding the package specified

```

apt-get install amule

```

---

### Post by feralert on 2005-01-08
Hi Sniffer,

Id rather recommend you to stick to [aMule](http://www.amule.org) as well. Ive been using it for quite a while and have to say that amule 2.0 rc7 was very stable (havent tried rc8 yet).
What i always do is compile everything from source, folowing [their instructions](http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian).

I have never tried it on ubuntu, but worked fine compiling from source in mandrake and FC3.

Besides, if you have any trouble at all, visit [aMule's forums](http://forum.amule.org/), which are always a very good help.

Good luck!

---

### Post by Sniffer on 2005-01-08
Thks for all the tips and replys.

Its getting a little bit annoying this freeze problem...tough i will persist :)


I have ubuntu installed as well in my laptop and works 100%, no freeze, no problem whatever....

In my server...is that i have told..will try the purge option and then if don't work the install from the source.....

---

### Post by Cordate on 2005-05-21
I've been having the same problem (though I'm running Hoary). Amule 2.0.0rc7 seemed to work fine for the first week, as I remember- I let it run for days. But now I have trouble running it for an hour without it freezing up the whole system. 

[QUOTE=ulrich]
have you tried to start with a fresh install?

```

apt-get --purge amule

```
purge kicks everything regarding the package specified

```

apt-get install amule

```[/QUOTE]

I'm trying this right now... I'll let you know how it goes :) 

By the way, the code we want for the purge should be:

```
sudo apt-get remove --purge amule

```
I tried it without the "remove" and bash didn't know what to do :)

-Cordate

---

### Post by Cordate on 2005-05-22
Well, I purged and reinstalled straight from the source (deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule) and still had the same troubles. They've just released a new version three days ago (possibly fixing this very bug) so I am going to go try that and we'll see what happens :) 

[Amule 2.0.1](http://www.amule.org/)

---

### Post by Sniffer on 2005-05-22
[QUOTE=Cordate]Well, I purged and reinstalled straight from the source (deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule) and still had the same troubles. They've just released a new version three days ago (possibly fixing this very bug) so I am going to go try that and we'll see what happens :) 

[Amule 2.0.1](http://www.amule.org/)[/QUOTE]


Just keep us informed...Now i'm using hoary but only in my laptop..so no amule needed.

Yep my server is infected with win32.....So that kind of info is vital to me..to take another shot.

---

### Post by Mellon on 2005-09-08
do you guys solve that problem?

i need help to solve it. 

im using haory for amd64 with not luck yet.

---

