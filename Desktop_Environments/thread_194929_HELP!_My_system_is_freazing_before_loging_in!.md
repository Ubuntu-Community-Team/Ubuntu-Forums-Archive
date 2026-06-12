---
title: "HELP! My system is freazing before loging in!"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Isoss on 2006-06-12
I installed some programs with synaptic and automatix then I rebooted and after the dual boot it froze where Kubuntu logo appears after starting some applications and it stands there forever!!](*,)  I went to the recovery mode and endited the sources.list and found that they were changed to breezy while I have dapper! (probably automatix did that) so I redited them and ran update and everything went ok then removed ubuntu-desktop and kubuntu-desktop then reinstalled both to no avail cuz I rebooted after that and still freezing.
PLEASE HELP ASAP!

Thanks.

---

### Post by an.echte.trilingue on 2006-06-12
If you don't have too much invested in your system already, it is probably easiest to re-install.  If you are going to use automatix, make sure you have the right one.

You need to do:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If that does not work you need to let us know exactly what what you tried to install with automatix.

---

### Post by Isoss on 2006-06-12
I had to reinstall! I don't know what's the problem! but this is the only thing that buggs me in linux! maybe because I'm not an expert yet but I've tried to make a full back up before using partimage but that too caused a problem! anyway, me and linux are still friends :mrgreen:  cuz me and windows can't be friends no more :???: So, thanks anyway. But I dunno what is the right automatix for dapper, is there one? I mean I had it in some backed-up downloaded packages so I used the onld one. I guess I'll have to look for the one made with dapper repositories! 

I will also apprciate your help  finding it;)

By the way. How can I backup the downloaded packages which are usually downloaded by synaptic So if I had to reinstall ubuntu one day I could easily use them and install the packages with synaptic without the need for downloading the packages again?

If that is possible I'd so much appriciate your help.

---

### Post by traveller.ct on 2006-06-12
[quote=Isoss]By the way. How can I backup the downloaded packages which are usually downloaded by synaptic So if I had to reinstall ubuntu one day I could easily use them and install the packages with synaptic without the need for downloading the packages again?[/quote] 
Downloaded packages are usually stored in [FONT=Courier New]/var/cache/apt/archives/[/FONT] and partially downloaded packages are usually stored in [FONT=Courier New]/var/cache/apt/arhives/partial/[FONT=Verdana] . You could back up these packages and put them back at the exact same places later for reuse.[/FONT][/FONT]

---

### Post by lamego on 2006-06-12
You should use [easyubuntu](http://easyubuntu.freecontrib.org/). Automatix can cause serious and hardly reversible problems with your installation.

---

### Post by Isoss on 2006-06-12
[quote="traveller.ct"]Downloaded packages are usually stored in /var/cache/apt/archives/ and partially downloaded packages are usually stored in /var/cache/apt/arhives/partial/ . You could back up these packages and put them back at the exact same places later for reuse.
[/quote]
That is just what I need, thanks a lot.
[quote="lamego"]
You should use easyubuntu. Automatix can cause serious and hardly reversible problems with your installation.
[/quote]
I used easy ubuntu but it just updated my repositories into breezy! besides, I need automatix it's good and just has what I want. I guess I'll have to look for the dapper version. Does easy ubuntu also have a dapper version?

---

