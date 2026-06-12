---
title: "I would really like to stick with Linux, but..."
date: 2006-01-11
forum: Desktop Environments
---

### Post by scottkennedy on 2006-01-11
Hi there...new to all of this.  Commandeered an old PC from a family member, and decided to install Ubuntu.  Like all of it, but have had some trouble installing a linux driver for my modem.  Finally got that sorted, and now have trouble easily "controlling" it.  I'd like it to dial up when I start email (evolution) or internet (mozilla), and hang up when those are closed.

While it SOUNDS straightforward to me, I cannot seem to find an easy fix.

By the way...constructing scripts is not really my deal...if this involves too much of that sort of activity, I'll just install Windows, and save some money for an IMAC.

A little help?

---

### Post by blueturtl on 2006-01-11
This should really in the support section and not in the Community Chat. Also nobody is obligated to help, so threatening to leave Linux is not really going to compell anyone to help. You have to give spesific details of your problem and hope there's someone with enough knowledge and time to respond! It's kind of like using the word 'please'. Difficult at first, but you'll be delighted at the results...

Also.. if Windows is so much easier why aren't you using it?

Excuse me for this rude response, but I'm getting tired of all the threads starting "Linux isn't ready... " or "I would like Linux if it did everything for me..." ;-)

---

### Post by scottkennedy on 2006-01-11
Well...first of all, I wasn't trying to be rude...just recognising the state of my own skills (low) in programming, coding, and such.

I'm just saying that if that is what is required to survive with Linux/Ubuntu, I don't have the skillset.

Sorry if the "a little help?" reference was too vague...I just feel a bit like a kid who has kicked his ball over the fence.  Hoping there's someone on the other side who'll throw it back.

Oh, by the way...the instructions suggested I make a post right away in the "community chat" forum...couldn't think of anything else to say.

---

### Post by Stormy Eyes on 2006-01-11
**scottkennedy**, are you looking for [dial on demand](http://www.google.com/search?q=linux+ppp+dial+on+demand&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official) for your modem? It's possible under Linux; I had it working a year ago, but have since moved to broadband. It *is* a bit complicated, as you have to hack config files.

---

### Post by John.Michael.Kane on 2006-01-11
Frist try looking this over [http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)
also have a look at [https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29%7C%28dialup%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29%7C%28dialup%29) [http://handsonhowto.com/dodip.html](http://handsonhowto.com/dodip.html)

if you have any other issues. please post in the right section of the forum.

And welcome to Gnu/Ubuntu/Linux

---

### Post by DigitalDuality on 2006-01-11
I don't know  your particular scenario, but just get broadband.  Unless you're out in a rural area where it's not offered, i don't see the problem in that.

Broadband is available for equal, and sometimes even lower prices than dial-up is nowadays.

For instance, AOL dial-up runs my parents about 24-25 a month.  I pay that for 10Mbps DSL. (normally averages out to 8Mbps).

---

### Post by Iowan on 2006-01-11
I'd REALLY like to point you at FREESCO, a single-floppy linux (2.0.39) router that has built-in dial-on-demand... but that would be a bit tacky on the Ubuntu forum.

---

### Post by aysiu on 2006-01-11
[QUOTE=DigitalDuality]I don't know  your particular scenario, but just get broadband.  Unless you're out in a rural area where it's not offered, i don't see the problem in that.

Broadband is available for equal, and sometimes even lower prices than dial-up is nowadays.[/QUOTE] I second the motion, for several reasons (besides the neglible price difference):

1. Ubuntu and many other Linux distributions use package managers to install software, and those package managers are heavily reliant on online repositories. If you're using dial-up, software installation and OS upgrades will take a painfully long time to execute.

2. Generally, it's easier to set up broadband than dial-up in Linux distributions--in fact, most of the time, Ubuntu will just automatically set it up for you... no fuss.

3. Uh... it's faster. It just makes your entire internet experience more pleasant.

---

### Post by xequence on 2006-01-11
> Also.. if Windows is so much easier why aren't you using it?

Maybe they are mentioning linux is harder, but its worth it to use a technically better OS, and thats why they are asking a question.

---

### Post by Lord Illidan on 2006-01-11
[quote=aysiu]I second the motion, for several reasons (besides the neglible price difference):

1. Ubuntu and many other Linux distributions use package managers to install software, and those package managers are heavily reliant on online repositories. If you're using dial-up, software installation and OS upgrades will take a painfully long time to execute.

2. Generally, it's easier to set up broadband than dial-up in Linux distributions--in fact, most of the time, Ubuntu will just automatically set it up for you... no fuss.

3. Uh... it's faster. It just makes your entire internet experience more pleasant.[/quote]

What's more, it will benefit ALL your operating systems, so even if you move to Windows, you will find a nice fat broadband trunk to download things from...

And the speed is indeed gratifying. Also, you can use a router to share the connection with other pcs, like I have at home.

---

### Post by poofyhairguy on 2006-01-11
Moved to correct forum.

---

### Post by ssam on 2006-01-11
i can't remember offhand what the dialup and hangup commands are. is it pppon and pppoff? if so
```
pppon && firefox && pppoff
```
would do the job. (although it may not hang up if firefox crashes (can a bash guru confirm?))

try running that in a terminal (replacing pppon and pppoff with the correct commands.)

if it works make add a custom application launcher to you panel

---

### Post by datacles on 2006-01-11
[QUOTE=xequence]Maybe they are mentioning linux is harder, but its worth it to use a technically better OS, and thats why they are asking a question.[/QUOTE]

Let's not forget that "anyone" can "use" an operating system!  My son was "using" Macintosh at the ripe age of 5 and that was .... many years ago, nevermind how many.  Linux IS harder, so is learning a foreign language, but I think there is so much more gratification when one surpasses a challenge.  The greatest challenge Window$ poses is trying to cough up enough cash to pay for all of the license fees!

---

### Post by jerrykenny on 2006-01-11
Scott,  just got   System > Administration > Networking, then either Add this Launcher to Panel, or Desktop,  you'll then have a handy icon for enabling / disabling your modem (after providing a password)

---

### Post by Suger on 2006-01-12
Just to confirm that  pppoff (if it's the right command) will not be executed if firefox crashes in
```
 pppon && firefox && pppoff 
```

Oh, and FWIW, my two years old son is "using" OpenBSD.

---

### Post by SickTwist on 2006-01-12
[QUOTE=ssam]i can't remember offhand what the dialup and hangup commands are. is it pppon and pppoff? if so
```
pppon && firefox && pppoff
```
would do the job. (although it may not hang up if firefox crashes (can a bash guru confirm?))

try running that in a terminal (replacing pppon and pppoff with the correct commands.)

if it works make add a custom application launcher to you panel[/QUOTE]

This should work, even if Firefox crashes although I do not know if "pppon" and "pppoff" are indeed real commands:
```
#!/bin/sh
pppon; firefox; pppoff
```

---

