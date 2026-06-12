---
title: "HELP! Can't install TA Spring"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by djay1991 on 2008-02-17
I have tried installing Spring as per the instructions on their install page, but at the first line I get errors. I am a fairly new Linux user and would appreciate any help.

djay@djay-desktop:~$ wget -q [http://buildbot.no-ip.org/~yokozar/apt/387EE263.gpg](http://buildbot.no-ip.org/~yokozar/apt/387EE263.gpg) -O- | \
>     sudo apt-key add -
[sudo] password for djay:
gpg: no valid OpenPGP data found.

---

### Post by jorgerosa on 2008-02-17
[http://spring.clan-sy.com/wiki/SetupGuide#Ubuntu](http://spring.clan-sy.com/wiki/SetupGuide#Ubuntu)
or
[http://blog.racoon97.net:81/installation-de-ta-spring-076b1-sous-ubuntu/](http://blog.racoon97.net:81/installation-de-ta-spring-076b1-sous-ubuntu/)
you can check for more games here:
[http://ubuntuforums.org/showthread.php?t=427205](http://ubuntuforums.org/showthread.php?t=427205)

---

### Post by Vadi on 2008-02-17
Their server for Ubuntu downloads is down last I remember.

---

### Post by djay1991 on 2008-02-17
Thanks for the links but I've already followed these guides the problem is when I enter the first command I get:
 
gpg: no valid OpenPGP data found

I've been googling the problem and can't find anything.

---

### Post by djay1991 on 2008-02-17
Thank you Vadi any idea when of if they will be coming back up

---

### Post by Vadi on 2008-02-17
No, they did say anything at all. This is the thread to follow:

[http://spring.clan-sy.com/phpbb/viewtopic.php?f=20&t=12469](http://spring.clan-sy.com/phpbb/viewtopic.php?f=20&t=12469)

See the ending of it. I'm waiting too for the game

---

### Post by Vadi on 2008-02-21
Good news - the guys are getting a Launchpad PPA up. I'm trying it out right now to see how it works, and will let you know when the instructions have been updated.

---

### Post by boombox1387 on 2008-02-29
It looks like the Launchpad PPA is up and the [setup guide]("http://spring.clan-sy.com/wiki/SetupGuide#Ubuntu") has been updated, but when I follow the instructions I get the "gpg: no valid OpenPGP data found" error.

Any suggestions?  Anyone else having this problem?

---

### Post by SandmanXC on 2008-03-01
I'm also having the exact problem :(. Please advise!

---

### Post by boombox1387 on 2008-03-01
I think [this thread from the Spring forum]("http://spring.clan-sy.com/phpbb/viewtopic.php?p=262539#p262539") fixes our problem.  Basically, if you add
```
deb http://ppa.launchpad.net/spring/ubuntu gutsy main
```
to System > Administration > Software Sources > Third-Party Software, it should add the Spring packages to Synaptic.

When I added the "deb" line it still gave me the gpg error, but it added the packages to Synaptic and I managed to install them, so it looks like it works so far.

---

### Post by Vadi on 2008-03-01
Yeah, the wiki instructions just copy/pasted the new url, which doens't work with a PPA.

I'm a bit hesitant to fix that yet since the PPA doesn't have the mods yet, only the engine + client + maps. Need ze mods now!

If you want though, you can download them yourself - they go into the ~/.spring/mods folder. Here are several sites hosting them:

- from JJ: [http://spring.jobjol.nl](http://spring.jobjol.nl)
- from Sefidel: [http://www.springplayersclub.com/](http://www.springplayersclub.com/)
- from AF: [http://www.darkstars.co.uk/downloads/](http://www.darkstars.co.uk/downloads/)
- from M_A_D: [http://www.tasdownloads.com/](http://www.tasdownloads.com/)
- from BLC: [http://spring-portal.com](http://spring-portal.com)
- from FA: [http://evolutionrts.info/maps/](http://evolutionrts.info/maps/)

---

### Post by argie on 2008-03-02
IIRC, [Yokozar]("https://launchpad.net/~scottritchie") is the person doing the packages. In that case, they'll probably be signed with his key, which you can get by following links from his launchpad page or by just going here:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x58403026387EE263](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x58403026387EE263)

Or you can just download the attachment, extract it and import that file from Settings » Repositories » Authentication » Import Key in Synaptic. Getting the key from the keyserver is just a better idea anyway.

---

