---
title: "Leadtek WinFAst TV2000 install"
date: 2006-03-04
forum: Desktop Environments
---

### Post by yetanotherpunter on 2006-03-04
Hey guys i have been trying to get my Leadtek WinFAst TV2000 to install for an age now, have put it in and it ran ok on my old Windows installation. 

I have worked though [Corey's TvTuner Guid]("http://www.linuxhelp.ca/guides/tvtuner/")e (exept the bits modifying the kernal as hal-device-manager says the kernal shows the card as present and has identified it). and also the HOWTO with mythTV. 

yet when i try tvtime-scanner i get:-

"
/root/.tvtime/stationlist.xml: No existing PAL station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.
"

Apparently setting this up is meant to be easy - am i missing somthing?

---

### Post by toganet on 2006-03-11
I have this card working with tvtime, and I think the trick was passing some parameters to the bttv module, something like:
[FONT="Courier New"]modprobe bttv tuner=9 card=34[/FONT]

I'm pretty sure those are the values, but ymmv.

---

### Post by yetanotherpunter on 2006-03-16
many thanks as soon as i can get back into ubuntu i will give it a try

---

### Post by toganet on 2006-03-18
[QUOTE=toganet]I have this card working with tvtime, and I think the trick was passing some parameters to the bttv module, something like:
[FONT="Courier New"]modprobe bttv tuner=9 card=34[/FONT]

I'm pretty sure those are the values, but ymmv.[/QUOTE]

I double-checked my configuration, and it turns out I was mistaken -- the tuner is actually 43, so your options line would be like:

```
options bttv card=34 tuner=43
```

---

### Post by linbetwin on 2006-03-18
I have a WinFast 2000 XP and it works "out of the box" with tvtime, zapping and xawtv. Never tried mythtv though.

---

### Post by nikoPSK on 2007-09-27
hmmm.... I think this [http://www2.truman.edu/~dat725/htpc_preface.html]("http://www2.truman.edu/~dat725/htpc_preface.html") might help.:)

---

