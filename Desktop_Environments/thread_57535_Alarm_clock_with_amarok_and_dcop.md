---
title: "Alarm clock with amarok and dcop"
date: 2005-08-16
forum: Desktop Environments
---

### Post by JLTB on 2005-08-16
Hi,

I recently discoverd some of the really cool stuff you can do with dcop, and here's one of the more useful things I've found  :).

I'm sure any of the veterans will know this is fairly simple stuff, but I found it really useful and maybe someone else will do the same. 

Well, recently my radio alarm clock started acting up and I thought .. hmmm .. maybe i should give the 'ol computer alarm clock a try again.  From past experience, however, I remembered that the problem with computer alarm clocks is that you can't be very sure your volume is set correctly to wake you up each morning (most computers have about 5 volume controls, counting hardware, soundcard, OS, media app, etc.).

KDE, as I just found out, lets you tweak all this stuff via dcop!  For those who don't know, dcop is layer in KDE that lets applications talk to eachother and control eachother.

So, here's what I've done.  Using KAlarm I've set up a typical alarm clock routine and set it to run a command when the alarm goes off.  The command I'm using currently is the following:

```

amarok ./music/wakemeup.m3u; dcop amarok player setVolume 100; dcop amarok player play

```

This command could be modified to do more advanced stuff, but right now what it does is: 1) load my wake up playlist in amarok (this ensures amarok runs if it is closed), 2) sets amarok's volume to full, 3) starts playing soothing wake up music at me :).

As I said, this could be easily modified to do more advanced stuff like up the system volume, unmute volume, etc., but I haven't tried that yet.

Well, maybe this will help someone :)

PS: You can manipulate most apps in KDE with dcop!  Have fun!

---

### Post by Mishura on 2005-08-17
Any good resources for DCOP?  I've played with a few I've seen in Google.. but they're mostly basic stuff.

---

### Post by thomax on 2005-08-17
It's always fun playing around whith this stuff, certainly when it are hollidays and I have nothing else to do :)

---

### Post by odrop on 2005-08-17
[QUOTE=Mishura]Any good resources for DCOP?  I've played with a few I've seen in Google.. but they're mostly basic stuff.[/QUOTE]

Mostly I think its just figuring out what applications have what dcop interfaces and then doing something fun with it.  The program kdcop  gives you an easy to use interface to play around with it.  I've been writing some python scripts that interact with kde programs, its pretty easy stuff once you get the hang of it.

---

### Post by JLTB on 2005-08-17
Good to know some other people find this stuff neat too.  I tried explaining why this is cool to my gf and all I got back was "you're such a geek" (in a loving way of course).

But geeks have all the fun right??

---

### Post by GeneralZod on 2005-08-18
[QUOTE=odrop]The program kdcop  gives you an easy to use interface to play around with it. [/QUOTE]

Woo - this is awesome! You can drag entries onto the konsole and it fills out the command template for you, too!

---

### Post by odrop on 2005-08-18
[QUOTE=GeneralZod]Woo - this is awesome! You can drag entries onto the konsole and it fills out the command template for you, too![/QUOTE]

What's even better, is it supports mulitple languages, shell, C++ and python, all you have to do is drag and drop for whatever language you're working with and it does it easily for you.  Very cool app.

---

### Post by JLTB on 2005-08-18
hmm!  I'd never used kdcop before.  Thanks!

---

### Post by x64Jimbo on 2007-05-22
Thanks! :) I woke up to Rage Against the Machine - Wake Up. ;)

---

### Post by nautaforever on 2008-07-09
thanks for the info. its really going to help a heavy sleeper like me

---

