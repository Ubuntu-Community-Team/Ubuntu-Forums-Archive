---
title: "Asus 1015pem netbook, fast OS"
date: 2013-03-25
forum: Desktop Environments
---

### Post by kraylus on 2013-03-25
greetings all! long time no see!

i need to put ubuntu on my netbook so i can tinker with it at work. i've started android app development as a side project from my regular job here in the shipping department. i came up with a sweet idea for an app that would streamline my whole department and the way we work. last time i had ubuntu on my netbook was with version 11.04 and it was slower than molasses in january. i'd like to put ubuntu back on there because for the life of me, i CANNOT get the android sdk to install correctly on my windows OS. however... i don't want to run unity in all its slow glory. but... i DO want to keep gnome. and i need it to be responsive. can't be having a bogged down system.

i suppose my question is... is there an ubuntu installation that accommodates all that? a fast gnome gui, without excessive processes idling in the background? its just gonna be a development environment....

the netbook is an asus 1015pem (the first dual-core atom processor). upgraded to 2gb of ram. it's a slow machine, granted, but i've run windows 7 on it without any real issue. cant run minecraft worth a **** in either windows or linux (marginally better in linux, but still unplayable).

ideally, i'd like to have a slackware or gentoo type distribution but long gone are the days where i could spend entire weekends compiling my own bootstrap and kernel and set everything up manually. i just don't have the time to relearn all that stuff. s'where ubuntu comes in. but i need a fast one!

please advise.

---

### Post by matt_symes on 2013-03-25
Hi

Install Xubuntu or even lighter Lubuntu. The links are at the top of the forum under "Ubuntu Community".

Kind regards

---

### Post by ajgreeny on 2013-03-25
> **kraylus said:**
>  i don't want to run unity in all its slow glory. but... i DO want to keep gnome. and i need it to be responsive. can't be having a bogged down system.

i suppose my question is... is there an ubuntu installation that accommodates all that? a fast gnome gui, without excessive processes idling in the background? its just gonna be a development environment....

please advise.
Do you *really* need gnome?

Why not look at the alternatives such as Xubuntu or Lubuntu.  If needed you can install anything else that's in the repos on any of the *ubuntu family of OSs, so if there is something in gnome that you have to have installed, simply go and get it from the repos with synaptic or software-centre.

---

### Post by kraylus on 2013-03-29
> **ajgreeny said:**
> Do you *really* need gnome?

Why not look at the alternatives such as Xubuntu or Lubuntu.  If needed you can install anything else that's in the repos on any of the *ubuntu family of OSs, so if there is something in gnome that you have to have installed, simply go and get it from the repos with synaptic or software-centre.

i dont NEED gnome, but i'm most comfortable using that environment. back in my gentoo/slackware days i was a big proponent for fluxbox and e16 (never was able to get e17 working). as gnome and kde became more and more popular, the compatibility of apps with lesser-known gui's started to decline. it got to the point where the only way to get things to behave right was to conform and install gnome or kde. seeing as how i cant stand kde, i went with gnome.

as far as xfce... that gui ain't what it used to be. i remember using it on freebsd about ten years ago and it was nice and fast. now it doesn't seem to be that much lighter than gnome. i could be wrong, as i'm just going by perceived performance.

the way i see it, most of the apps i'll be using are most likely gnome apps. so even if i'm using fluxbox, i'm still going to be loading a ton of gnome libs into memory, no? why not load a few more and get the gui that makes it all work nice :D

granted, i've been out of the linux loop for quite some time, so that all may have changed. i just don't want to try out a bunch of guis. last time i did that, ubuntu broke and i had to reinstall.

if i am wrong, please educate me! dont be afraid to tell me that ubuntu may not be what i'm looking for. it does seem to be a bit bloated compared to other distros, but that is the price one pays for convenience i suppose....

---

### Post by kraylus on 2013-04-03
ok, so i went with lubuntu in the end. turns out, it's actually pretty nice. i keep finding myself trying to resist the urge to heavily customize it. that's when i start installing things like compiz and it all goes downhill from there.

im tackling wireless printing at the moment, but i don't think i'm going to have much luck. everything else seems to be working rather well.

thanks everybody for their input!

---

### Post by mamamia88 on 2013-04-03
You'd be surprised how easy it is to setup wireless printing.  I set it up the other day in xubuntu and all i needed to know was the username, password, and printer model of the win 7 pc where the printer is hooked up.    Took all of 5 minutes.

---

### Post by ibjsb4 on 2013-04-03
>  i keep finding myself trying to resist the urge to heavily customize it

[Resistance is futile :P]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=customize+lubuntu&sa=Search&cof=FORID:9")

---

### Post by kraylus on 2013-04-06
> **mamamia88 said:**
> You'd be surprised how easy it is to setup wireless printing.  I set it up the other day in xubuntu and all i needed to know was the username, password, and printer model of the win 7 pc where the printer is hooked up.    Took all of 5 minutes.

unfortunately for me, setup was not so easy. then again, it might have had something to do with the gui front-ends that lubuntu offers by default. i had to scour google pretty hard to get my particular printer working. i ended up [writing this post]("http://ubuntuforums.org/showthread.php?t=2132122") in case anyone else had similar issues. in my setup, my printer is not hooked up to any pc, it's connected directly to the router wirelessly. so the standard samba-style printer setups won't work for me.

perhaps if i had gone with regular, old ubuntu with all its latest features, printer setup would have been a bit more automated. i also notice other small things that i take for granted. like, the mouse cursor disappearing when you start typing. or the touchpad disabling when you start typing. these things are not really addressed in the openbox gui. i've had to come up with silly workarounds that don't always function properly.

fortunately, i can live without these things. i hadn't really noticed they were there until after i had setup my lamp server for my scripting. i may end up either installing the gnome gui on here or just wiping this install and putting the new ubuntu on here. time will tell.

---

