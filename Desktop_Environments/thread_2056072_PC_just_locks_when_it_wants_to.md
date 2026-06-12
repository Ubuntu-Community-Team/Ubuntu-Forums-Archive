---
title: "PC just locks when it wants to"
date: 2012-09-10
forum: Desktop Environments
---

### Post by TheTopcat on 2012-09-10
Ok sorry if this has been covered but just don't have a clue as to what the fault is apart from the symptoms.

I have a pc with 4gig ram q6600 cpu and I have installed Ubuntu 12.04 and then installed KDE I have added several applications including Compiz and cairo-dock the reason I have brought them up is that I have seen lots of problems with them on forums.

The machine for no reason will just Lock up and the only way is to power down and Power up the machine.

I am a windows user that's moved over to linux so I  am new at this, I could do with some advice or help on what I can do to diagnose the problem.

any help would be great
IAN UK

---

### Post by Epodx64 on 2012-09-10
Are you overclocking at all? also try running memtest86 to make sure your rams good I had some bad ram that worked most of the time but had strange random problems like lockups and just little errors with things random crashes sometimes kde would just kinda disappear.

---

### Post by Frogs Hair on 2012-09-10
Any reason why you chose Compiz over Kwin for desktop effects ? Kwin is native to KDE and I was wondering if you are having graphics problems or a conflict of some kind.

---

### Post by Epodx64 on 2012-09-11
> **Frogs Hair said:**
> Any reason why you chose Compiz over Kwin for desktop effects ? Kwin is native to KDE and I was wondering if you are having graphics problems or a conflict of some kind.

That's a good point I didn't put Kwin + Compiz together at first glance I'd imagine that might cause some instability.

---

### Post by TheTopcat on 2012-09-14
Thanks for the response not heard of kwin before I will check that out, also I will run the mem test and get back to you all asap.

---

### Post by TheTopcat on 2012-09-14
I am doing a mem check on the system as I type, Just for one min lets say its compiz can some one please direct me to an set up guide where I can install compiz on KDE to allow applications like Cairo dock to work with out that Black Box showing behind it.

Many thanks for any help on this, as I am still getting to grips with all of this please can you give me any help in very simple steps as I have only been using Linux for 12months.

Many Thanks
IAN (UK)

---

### Post by RichardUK on 2012-09-14
I experience that on a fresh install about a year ago, turned out the new SSD I had brought was failing. Did just what yours is doing, hard locked. Power cycle only way to bring it back. After about two weeks SSD failed completely. New HD and problem was gone. So I would suggest do a backup just in case is the same issue.

---

### Post by dodo3773 on 2012-09-14
The majority of the lockups I have had have always been from compositing effects. Try turning all the effects way down and see if you still have issues (or run a window manager that does not support them to test (like openbox)).

---

### Post by Epodx64 on 2012-09-14
I had lockups because of bad ram before as well try

sudo dmidecode --type memory

and post it back here.

---

### Post by RJARRRPCGP on 2012-09-15
Having too high of a core OC is a common cause.

---

### Post by markMDW on 2012-10-13
Ive got a COMPAQ AMD-64 laptop now running Ubuntu 12.04 using compiz because of its graphics card capabilities.  It locks up periodically, unable to ctrl alt f1 into a tty (the mouse moves around though).  There isn't a fix because the problem is compiz as I understand it, which is required by Unity. I'm beginning to get use to it and hate to uninstall it now.  

But I can't do any serious work with my laptop now with Ubuntu 12.04 on it, but its great for running Firefox, Chromium and Thunderbird.. for reading only.    I've been burnt with losing data in LibreOffice.

On the other hand, Ubuntu 10.04 is ROCK SOLID.  Ubuntu 10.04  absolutely never gets in a total freeze.  If an application does lock, I can always open a terminal and resolve it.

I'd like to keep Ubuntu 12.04 of this laptop if I could install some tool that resets the lock, and saves my data.  Is there such a thing?

Otherwise, I'm going to install Xubuntu or Ubuntu 10.04 for stability and productivity. 

IMO, if compiz is indeed the culprit, then I have to say it was a mistake to ever design an operating system that depends upon it.  No one serious about doing work could consider using it.  It'd be better off for Canonical if the user gets a message that says "incompatible with Unity" than the user installs a system that seems to work great... most of the time.  Once lose data due to lock ups, they aren't going to be able to depend upon it.

---

### Post by Insomn1a on 2012-10-14
> **markMDW said:**
> Ive got a COMPAQ AMD-64 laptop now running Ubuntu 12.04 using compiz because of its graphics card capabilities.  It locks up periodically, unable to ctrl alt f1 into a tty (the mouse moves around though).  There isn't a fix because the problem is compiz as I understand it, which is required by Unity. I'm beginning to get use to it and hate to uninstall it now.  

But I can't do any serious work with my laptop now with Ubuntu 12.04 on it, but its great for running Firefox, Chromium and Thunderbird.. for reading only.    I've been burnt with losing data in LibreOffice.

On the other hand, Ubuntu 10.04 is ROCK SOLID.  Ubuntu 10.04  absolutely never gets in a total freeze.  If an application does lock, I can always open a terminal and resolve it.

I'd like to keep Ubuntu 12.04 of this laptop if I could install some tool that resets the lock, and saves my data.  Is there such a thing?

Otherwise, I'm going to install Xubuntu or Ubuntu 10.04 for stability and productivity. 

IMO, if compiz is indeed the culprit, then I have to say it was a mistake to ever design an operating system that depends upon it.  No one serious about doing work could consider using it.  It'd be better off for Canonical if the user gets a message that says "incompatible with Unity" than the user installs a system that seems to work great... most of the time.  Once lose data due to lock ups, they aren't going to be able to depend upon it.

Try using unity 2D, that uses metacity instead of compiz. if you log out and click on the ubuntu logo next to the password prompt, it will give you the option to use ubuntu (2D)

---

### Post by markMDW on 2012-10-18
Will give that a try this weekend and post on how well it works.  Thanks for the advice

---

