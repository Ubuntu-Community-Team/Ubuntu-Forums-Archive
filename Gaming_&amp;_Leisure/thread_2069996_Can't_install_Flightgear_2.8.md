---
title: "Can't install Flightgear 2.8"
date: 2012-10-11
forum: Gaming &amp; Leisure
---

### Post by gandalf3 on 2012-10-11
i added the playdeb repo to my sources, did sudo apt-get update and everything, but in synaptic and the software center it sill says 2.6?

installing from here

[http://www.playdeb.net/software/FlightGear](http://www.playdeb.net/software/FlightGear)

i have 12.04
:confused:
why???

---

### Post by cipherboy_loc on 2012-10-11
What is the exact line in your apt sources?


Thanks,
Cipherboy

---

### Post by gandalf3 on 2012-10-11
there's three:

[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games (source code)
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps

hey...
i just noticed the "oneiric ocelot" reference... going to try changing it.. (i hope that's what your supposed to do :P)

EDIT:

must be! it worked :biggrin:
Thanks!!

---

### Post by donteatthis on 2012-10-23
i have got similar problem. In my case the software center shows flight gear 2.4.0.1 version and not the current one. how can i rectify this? 

even going to the playdeb.net website and clicking on download icon prompts me to open software center with the same old version of Flight Gear. 

how can I download the latest version Ubuntu 12.04: 2.8.0-1~getdeb1 ?

---

### Post by donteatthis on 2012-10-23
problem solved! just click on this [link]("http://www.playdeb.net/updates/Ubuntu/12.04#how_to_install") and go through the steps.. its that simple... 

just wondering why i couldn't able to figure out earlier.

---

### Post by ptn107 on 2012-12-07
I have packaged Flightgear 2.8 for Ubuntu 12.10.  Give my ppa a try:

```
deb http://ppa.launchpad.net/ptn107/ppa/ubuntu quantal main 
deb-src http://ppa.launchpad.net/ptn107/ppa/ubuntu quantal main
```

---

### Post by gandalf3 on 2012-12-07
i might try it after i upgrade. 
(i'm running 12.04)
for now, playdeb works fine.
Thanks anyway :)

---

### Post by jarpiw on 2012-12-08
> **ptn107 said:**
> I have packaged Flightgear 2.8 for Ubuntu 12.10.  Give my ppa a try:

```
deb http://ppa.launchpad.net/ptn107/ppa/ubuntu quantal main 
deb-src http://ppa.launchpad.net/ptn107/ppa/ubuntu quantal main
```

fgfs-base package is missing

guys, try that:
deb [http://mirrors.dotsrc.org/getdeb/ubuntu/](http://mirrors.dotsrc.org/getdeb/ubuntu/) quantal-getdeb games

---

