---
title: "fluxbox xession errors"
date: 2007-08-14
forum: Desktop Environments
---

### Post by bsunde on 2007-08-14
Every time I close a window I get an "apps file failure" xession error.  Anyone know what this is about?  I'm using fluxbox 1.0rc3.

---

### Post by kerry_s on 2007-08-14
it's fluxbox refresh. you can setup fluxbox to log to /dev/null. i forget what the exact line looks like in ~/.fluxbox/startup. you comment out the top "exec /usr/bin/fluxbox" and uncomment the bottom 1 for logging, change the path to save the log to /dev/null.

---

### Post by RedSquirrel on 2007-08-14
Funny. You asked about this in another thread, kerry_s, but I guess you missed my response somehow. No big deal. :)

Here's the answer:

Fluxbox expects to find the file ~/.fluxbox/apps, so just create that file and the error will disappear:

```
touch ~/.fluxbox/apps
```This is the file Fluxbox uses for storing application information, for example, dimensions and position if you choose to "remember" that information (right-click on title bar and select Remember...). If you haven't done that, then the file does not exist yet, and you get that silly error.

---

### Post by kerry_s on 2007-08-14
> **RedSquirrel said:**
> Funny. You asked about this in another thread, kerry_s, but I guess you missed my response somehow. No big deal. :)

Here's the answer:

Fluxbox expects to find the file ~/.fluxbox/apps, so just create that file and the error will disappear:

```
touch ~/.fluxbox/apps
```This is the file Fluxbox uses for storing application information, for example, dimensions and position if you choose to "remember" that information (right-click on title bar and select Remember...). If you haven't done that, then the file does not exist yet, and you get that silly error.

no, when i had that problem, i know i had ~/.fluxbox/apps, i traced it to some kind of refresh fluxbox was doing, so i just detoured fluxbox from filling up the xsession-errors. as far as i could find it was a fluxbox bug.
no big deal, i'm using jwm now, i really like how simple it is. i'm practicing on getting as minimal as i can, i'm planing on replacing this laptops hd with a cf card, the hd has been acting up so my guess is it's on it's way out. i bought the hd used for a couple of bucks, so no surprise there, when i bought the laptop the original hd was already dead.
anyways jwm is so simple it's pretty bullet proof, doesn't log anything, just works. i had to compile the latest to get the pretty 1 though, the repo 1 is old and not as good looking. :)

---

### Post by RedSquirrel on 2007-08-15
> **kerry_s said:**
> no, when i had that problem, i know i had ~/.fluxbox/apps, i traced it to some kind of refresh fluxbox was doing, so i just detoured fluxbox from filling up the xsession-errors. as far as i could find it was a fluxbox bug.

Interesting. I haven't seen the "apps file failure" issue on my system for a long time, and I was under the impression it occurred when I didn't have an apps file. It seemed to go away after I created one. Oh well.

That is one advantage of using the latest Fluxbox SVN--I haven't seen anything in my .xsession-errors related to Fluxbox for a long long time. :)


> **kerry_s said:**
> no big deal, i'm using jwm now, i really like how simple it is. i'm practicing on getting as minimal as i can, i'm planing on replacing this laptops hd with a cf card, the hd has been acting up so my guess is it's on it's way out. i bought the hd used for a couple of bucks, so no surprise there, when i bought the laptop the original hd was already dead.
anyways jwm is so simple it's pretty bullet proof, doesn't log anything, just works. i had to compile the latest to get the pretty 1 though, the repo 1 is old and not as good looking. 

That does look nice. I just can't let go of Fluxbox. :grin:

By the way, they are doing more work on rounded window corners in Fluxbox. I think they look a little better, but there's still work to be done (this is only Phase 1, according to the Changelog). In my opinion, this is an important feature. Rounded windows are ubiquitous.

---

### Post by kerry_s on 2007-08-15
that's pretty sweet, your rox-filer is pretty to.

Hey, you want to hear something funny, remember i did grandma's computer, it turns out now it's the fastest computer in the house, now she's complaining the grand kids won't leave it alone, they keep fighting over it. LOL. they love playing disneychannel, nickalodian, etc... baisicly flash based sites, on her computer the sites load so dang fast there's no waiting.

---

### Post by RedSquirrel on 2007-08-16
> **kerry_s said:**
> that's pretty sweet, your rox-filer is pretty to.

Thanks. It took a bit of digging to find out how to make the rox-filer background white. Apparently, you can use an image as well but I didn't bother. I normally use Tango icons, but I'm trying out Tangerine now. :)



> **kerry_s said:**
>  Hey, you want to hear something funny, remember i did grandma's computer, it turns out now it's the fastest computer in the house, now she's complaining the grand kids won't leave it alone, they keep fighting over it. LOL. they love playing disneychannel, nickalodian, etc... baisicly flash based sites, on her computer the sites load so dang fast there's no waiting.

That's a great story. It never ceases to amaze me what can be accomplished with a lightweight linux setup. Computers that normally would be collecting dust can be revived and turned into a truly useful and fast machine. This is just so much fun. :grin:

---

