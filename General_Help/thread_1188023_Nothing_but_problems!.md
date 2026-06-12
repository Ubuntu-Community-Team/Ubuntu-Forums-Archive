---
title: "Nothing but problems!"
date: 2009-06-15
forum: General Help
---

### Post by Stugol on 2009-06-15
I have recently - for the dozenth time in the past couple of years (yes, I'm a MASOCHIST!) - installed Ubuntu.

Leaving aside for the moment the majority of the MANY problems I've had with it in the 24 hours since installing it - like automatically destroying the Windows bootloader ON A DIFFERENT HARD DRIVE; or the fact that USB keyboards don't work in the recovery console - you know, minor stuff like that - I am now experiencing problems that completely prevent me using Ubuntu.

Okay, first of all my system specs. I'm using 32-bit Ubuntu Desktop 9.04 on a 64-bit dual-core system. Custom build - works fine in Windows. Fresh installation of Ubuntu, except that I also installed Synergy; and a printer.

Okay. Ubuntu comes up saying it wants to install system updates. I say ok. Halfway through doing that, the screen goes black and stays like that. And no, it wasn't the screen saver. So I hit reset. Then, after entering my username and password at the graphical login prompt, the login freezes. The mouse still works, and the shutdown menu at the bottom can still be used; but the password entry box remains and is non-responsive. Also, selecting shutdown or restart gives me a black screen and just freezes.

So, I use recovery options to repair the graphical config (I forget the exact name of the recovery option) and; when that doesn't help; I ask it to repair damaged packages.

Upon reaching the login screen again, I find that I can't use my mouse or my keyboard. Synergy is no longer running (presumably as a result of the package repair - I assume configfiles were reset to defaults) and I can't use my mouse or keyboard. So how the hell am I supposed to log in, or fix anything??

Seriously guys, I thought Linux was supposed to be STABLE? I installed it because I wanted a stable OS that didn't crash much; and I've had nothing but problems with the damn thing. Linux will NEVER be accepted by the world at large as a viable alternative to Windows until it's possible to use it for more than five minutes without breaking it.

Now, can anyone tell me what the hell I'm supposed to do; or should I just format the damn thing and reinstall Windows?

---

### Post by leandromartinez98 on 2009-06-15
Format everything and install Linux again. ;)

Either you have a broken download or broken installation, or some unsuported graphic card. Surely what you are experience is not what
most people do. By the way, if what you want is stability, go for
Hardy (although you should not have an unstable system with Jaunty,
of course).

---

### Post by scrooge_74 on 2009-06-15
Im not that good at some of the technicall aspects you are having problems with, but as a rule for me I never install the latest version of Ubuntu for a long time, Im still using 8.04 on all my equipments.

Erasing bootloaders is a mistake I used to do a couple of years ago, I would get confuse with the naming of drives in linux. I don't know if the fact of using the 32 bit on a 64 is having some effect on your installation (have no experience with 64)

Maybe you should install Synergy after you have everything else working

---

### Post by DeMus on 2009-06-15
> **Stugol said:**
> I have recently - for the dozenth time in the past couple of years (yes, I'm a MASOCHIST!) - installed Ubuntu.

Leaving aside for the moment the majority of the MANY problems I've had with it in the 24 hours since installing it - like automatically destroying the Windows bootloader ON A DIFFERENT HARD DRIVE; or the fact that USB keyboards don't work in the recovery console - you know, minor stuff like that - I am now experiencing problems that completely prevent me using Ubuntu.

Okay, first of all my system specs. I'm using 32-bit Ubuntu Desktop 9.04 on a 64-bit dual-core system. Custom build - works fine in Windows. Fresh installation of Ubuntu, except that I also installed Synergy; and a printer.

Okay. Ubuntu comes up saying it wants to install system updates. I say ok. Halfway through doing that, the screen goes black and stays like that. And no, it wasn't the screen saver. So I hit reset. Then, after entering my username and password at the graphical login prompt, the login freezes. The mouse still works, and the shutdown menu at the bottom can still be used; but the password entry box remains and is non-responsive. Also, selecting shutdown or restart gives me a black screen and just freezes.

So, I use recovery options to repair the graphical config (I forget the exact name of the recovery option) and; when that doesn't help; I ask it to repair damaged packages.

Upon reaching the login screen again, I find that I can't use my mouse or my keyboard. Synergy is no longer running (presumably as a result of the package repair - I assume configfiles were reset to defaults) and I can't use my mouse or keyboard. So how the hell am I supposed to log in, or fix anything??

Seriously guys, I thought Linux was supposed to be STABLE? I installed it because I wanted a stable OS that didn't crash much; and I've had nothing but problems with the damn thing. Linux will NEVER be accepted by the world at large as a viable alternative to Windows until it's possible to use it for more than five minutes without breaking it.

Now, can anyone tell me what the hell I'm supposed to do; or should I just format the damn thing and reinstall Windows?

So, just because you experience some problems, Linux (or in this case Ubuntu) is worthless? What nonsense is that? I used Hardy when it came out, I switched to Jaunty when it came out and I have a perfect system: stable, fast, does what it needs to do.
If you are so negative about Ubuntu you better go back to your Windows and stay there, enjoying the viruses, the malware, the addware, the so wonderful blue screens of death. But one thing, don't tell us Ubuntu is no good because it is good.

---

### Post by scrooge_74 on 2009-06-15
Dont be so rash on the dude, we here to help out, if he wants to vent out is anger or lack of skills on linux let him. 

You have no idea how many times I just wanted to thrown my PC out the window the first time I installed Debian Sarge and I had no clue what to do, took me 3 months to get the hang of it (yep Im a slow learner)

---

### Post by Cheesemill on 2009-06-15
> **Stugol said:**
> like automatically destroying the Windows bootloader ON A DIFFERENT HARD DRIVE; or the fact that USB keyboards don't work in the recovery console

Unless you specifically tell it otherwise, Ubuntu will always install the bootloader on the first hard drive, no matter which drive you choose to install Ubuntu on. If you want to change this just click 'Advanced' on the last page of the installer and tell it where you want the bootloader.

Also your USB issues are due to your computers BIOS settings, **not** Ubuntu.
Just go into your computers BIOS and look for an option called 'Enable USB legacy mode' (or something similar, it varies from machine to machine).

---

### Post by Odyssey1942 on 2009-06-15
Stugol,

I have been using Windows for 25+ years, and like you, wanted something better. Beginning several years ago, I also went through several versions of Linux, latest being Ubuntu starting back around versions 3 or 4 and when 8.04 came out, I decided it was time to make Ubunutu my main platform. While I have a (separate) Windows computer running beside my Ubuntu machine, I almost never use it and I am on the computer several hours daily.

Unless you have a specific need on a constant basis for Windows, try reinstalling only Ubunutu and I recommend 8.04 because of its rocklike stability (move to ver 9 AFTER you are sure you want to stay with Ubunutu). 

Using the great help available in the forum community, and doubtless DeMus will be happy to give you some assistance, you will quickly find the switch to flip that makes your problems go away. Then you can go back to a dual boot if you need Windows, though I find there is very little that Windows can do that Ubuntu cannot.

If your machine simply rejects Ubuntu, though I sincerely doubt that this will be the case, try picking up an older computer on the cheap and use Ubuntu only so that you can get some experience with Linux. You can run your computers side by side with one monitor, keyboard and mouse using an inexpensive KVM switch ($20-25).

Compared to Windows, I love the security and stability and knowing, not wondering, what will be the outcome when I give a command. Stay with it! I predict that you will make the move to Ubunutu. It is just a matter of getting past this initial hurdle.

---

### Post by DeMus on 2009-06-15
> **Odyssey1942 said:**
> Stugol,

I have been using Windows for 25+ years

????????????????????????????????????????????????????????????????????????
25 years????

How long is one year for you? 9 months or so?
Windows 3.1 came in 1991 if I am not mistaken and it was the first Windows you could actually use.
So in my calculation this is just 18 years ago?

---

### Post by Odyssey1942 on 2009-06-15
DeMus,

Well spotted! Should have read PC rather than Windows.

I bought my first "personal computer" an Apple in about 1979 or 80 (48K RAM + 16K RAM upgrade and a 64K floppy drive-well before hdd's for personal computers. Owned the first Apple computer in HongKong!

Then when IBM came out with the "PC" in about 1981, I switched and have used continuously since.

---

### Post by DeMus on 2009-06-15
> **Odyssey1942 said:**
> DeMus,

Well spotted! Should have read PC rather than Windows.

I bought my first "personal computer" an Apple in about 1979 or 80 (48K RAM + 16K RAM upgrade and a 64K floppy drive-well before hdd's for personal computers. Owned the first Apple computer in HongKong!

Then when IBM came out with the "PC" in about 1981, I switched and have used continuously since.

Sorry for the remark, couldn't help it.
Got my first pc at work in 1986, 2 5-1/4" floppy drives - no hard disk and a processor running on 4.77MHz. Wow.
Then an AT with a 20MB hard disk, impossible to fill so much storage, and 1MB extended/expanded memory.
Is it any better now? Quad-core processors, 4GB memory, 1TB hard disk and still we are waiting for the software to do what we want it to do.

But, what was this thread about? Oh yes, nothing but problems. They happen as long as there are computers.

---

### Post by Stugol on 2009-06-15
> **leandromartinez98 said:**
> Format everything and install Linux again. ;)

Yeah, very helpful. NOT!

I just bloody DID that. Twice. You really think it's acceptable to use an OS that you have to REINSTALL EVERY DAY? Or one where the OFFICIAL UPDATES break the machine?

> **leandromartinez98 said:**
> 
 Either you have a broken download or broken installation, or some unsuported graphic card. Surely what you are experience is not what
most people do. By the way, if what you want is stability, go for
Hardy (although you should not have an unstable system with Jaunty,
of course).

The system was working until the updates happened. How can I have an unsupported graphics card? It was WORKING BEFORE.

Oh, so I should use an OUTDATED version of Linux. What a stupid suggestion. Jaunty isn't a beta, therefore it should work. My question was how to make THIS ONE work, not how to use a DIFFERENT PRODUCT. If I'm gonna do that, I might as well use Windows. At least the damn thing WORKS.

---

### Post by Stugol on 2009-06-15
> **scrooge_74 said:**
> Maybe you should install Synergy after you have everything else working

Firstly, "everything else working" never happens. I'm always reconfiguring my system. By that reasoning, I'd never install it.

Secondly, you seem to be suggesting that Synergy is the cause of the problem. IT ISN'T. The bloody OFFICIAL UPDATES are the cause of the problem!

---

### Post by Stugol on 2009-06-15
> **DeMus said:**
> So, just because you experience some problems, Linux (or in this case Ubuntu) is worthless? What nonsense is that?

No, because I ALWAYS experience LOADS of problems with it. Either it doesn't like my graphics card; or I can't find drivers for my wifi adapter; or it won't access the Windows shares on my other machine; or I can't use remote-desktop; OR THE DAMN OFFICIAL UPDATES BREAK THE WHOLE MACHINE!!!!!

Seriously, don't you consider this to be a bit of a serious flaw?

> **DeMus said:**
>  I used Hardy when it came out, I switched to Jaunty when it came out and I have a perfect system: stable, fast, does what it needs to do.

Yeah? Well I don't. And, judging by the THOUSANDS of forum posts and Google results whenever I try to get help on a Linux problem, most people don't either.

> **DeMus said:**
> If you are so negative about Ubuntu you better go back to your Windows and stay there, enjoying the viruses, the malware, the addware, the so wonderful blue screens of death. But one thing, don't tell us Ubuntu is no good because it is good.

Um.... You can't throw the Blue Screen of Death at me when the problem I'm currently having is the LINUX SCREEN OF DEATH. Duh!

If Ubuntu is so good, how come the official updates render it completely unusable?

Tell me, how many Windows users change their screen resolution and suddenly CAN'T GET BACK INTO WINDOWS without posting on forums (which they can't do without a working computer) to ask how to edit their bloody X11 configs!!!???? How come this is considered reasonable behaviour in Linux?

Look, I'm TRYING to work with it here. I *want* to use ubuntu. But ubuntu doesn't want to work with me.

---

### Post by t0p on 2009-06-15
If you actually want some help, you need to post your machine's specs.  As many specs as you can think of.  It's impossible for anyone to know what to suggest if we don't know what hardware setup we're dealing with.  What you're experiencing is extremely unusual, but if someone here can help you, they will.

If you're just trolling, carry on.

---

### Post by Stugol on 2009-06-15
> **scrooge_74 said:**
> Dont be so rash on the dude, we here to help out, if he wants to vent out is anger or lack of skills on linux let him. 

You have no idea how many times I just wanted to thrown my PC out the window the first time I installed Debian Sarge and I had no clue what to do, took me 3 months to get the hang of it (yep Im a slow learner)

Thank you for your note of support.

But I don't think my lack of skills is the issue here. I think the issue here is that the OFFICIAL UPDATES broke my machine. Coz it stopped working, and I hadn't done anything else recently.

---

### Post by Stugol on 2009-06-15
> **Cheesemill said:**
> Unless you specifically tell it otherwise, Ubuntu will always install the bootloader on the first hard drive, no matter which drive you choose to install Ubuntu on. If you want to change this just click 'Advanced' on the last page of the installer and tell it where you want the bootloader.

Yeah, I figured that out. AFTER it had ruined my Windows installation.

> **Cheesemill said:**
> Also your USB issues are due to your computers BIOS settings, **not** Ubuntu.
Just go into your computers BIOS and look for an option called 'Enable USB legacy mode' (or something similar, it varies from machine to machine).

I don't think so. The keyboard works fine in other legacy environments - e.g. Spinrite; or a DOS boot CD.

But I will check anyway.

---

### Post by leandromartinez98 on 2009-06-15
> **Stugol said:**
> Yeah, very helpful. NOT!

I just bloody DID that. Twice. You really think it's acceptable to use an OS that you have to REINSTALL EVERY DAY? Or one where the OFFICIAL UPDATES break the machine?


The system was working until the updates happened. How can I have an unsupported graphics card? It was WORKING BEFORE.

Oh, so I should use an OUTDATED version of Linux. What a stupid suggestion. Jaunty isn't a beta, therefore it should work. My question was how to make THIS ONE work, not how to use a DIFFERENT PRODUCT. If I'm gonna do that, I might as well use Windows. At least the damn thing WORKS.

I recommend you try Valium ([http://en.wikipedia.org/wiki/Diazepam](http://en.wikipedia.org/wiki/Diazepam)), it helps in cases like yours.

---

### Post by Stugol on 2009-06-15
> **Odyssey1942 said:**
> 
Unless you have a specific need on a constant basis for Windows, try reinstalling only Ubunutu...


Yes, good plan. And then, when the automatic updates break the machine again - or something else happens - I won't have a computer at all! So I won't be able to visit this forum! So I'll be TOTALLY SCREWED!!!!!

Thank you. A *brilliant* idea. NARF! ZORT!

*sigh*

As it happens, I have another machine with Windows on it. But that's not the point. You didn't know that, yet you advised me to remove my only recovery option anyway. Don't you people THINK before you speak?

> **Odyssey1942 said:**
> ...and I recommend 8.04 because of its rocklike stability (move to ver 9 AFTER you are sure you want to stay with Ubunutu).


Okay, perhaps trying an essentially obsolete version of Ubuntu MIGHT be my best option. Can it be upgraded easily to 9.04 later on, without reinstalling from scratch?

> **Odyssey1942 said:**
>  Using the great help available in the forum community, and doubtless DeMus will be happy to give you some assistance, you will quickly find the switch to flip that makes your problems go away.

(...snip...)

Compared to Windows, I love the security and stability and knowing, not wondering, what will be the outcome when I give a command. Stay with it! I predict that you will make the move to Ubunutu. It is just a matter of getting past this initial hurdle.

Uhuh. Security. Stability. Initial Hurdle. Right.

Did I mention I can't even log in because my keyboard and mouse don't work? Did I? I'm sure I did. That doesn't sound like "stability" to me - or, for that matter, a "hurdle". It SOUNDS like a "serious fuckup" to me. God help me if it was my only machine.

---

### Post by leandromartinez98 on 2009-06-15
Try installing Slackware in your other machine (the one with Windows).

---

### Post by Stugol on 2009-06-15
> **t0p said:**
> If you actually want some help, you need to post your machine's specs.  As many specs as you can think of.  It's impossible for anyone to know what to suggest if we don't know what hardware setup we're dealing with.  What you're experiencing is extremely unusual, but if someone here can help you, they will.

If you're just trolling, carry on.

No, I'm not trolling. Yeah, okay, I'm annoyed, frustrated and almost completely out of patience with this so-called operating system. But I'm here for a solution.

Um...it's a dual-core AMD64 with a gig of DDR, I think, and three hard drives (1 IDE, 2 SATA).I'm not in front of it just at the second. When I am (tomorrow), I'll bring up Astra32 in Windows and tell you guys as much as possible about the machine.

---

### Post by t0p on 2009-06-15
> **leandromartinez98 said:**
> Try installing Slackware in your other machine (the one with Windows).

Or Debian.  You'd probably get on fine with Debian.

:p

Alternatively, you could reformat your hard drive and install some more Vista on the machine instead.  Windows 7 won't be much longer, perhaps you could install that.

It's strange how you have endless problems with Ubuntu when most of us don't.  If you wanted to persevere, and you stopped this "Linux is crap because I can't make it work" attitude, you'd find a lot of helpful folk in these forums.  Try us if you like.  Or don't.

---

### Post by Stugol on 2009-06-15
> **leandromartinez98 said:**
> I recommend you try Valium ([http://en.wikipedia.org/wiki/Diazepam](http://en.wikipedia.org/wiki/Diazepam)), it helps in cases like yours.

Meh. When you've been up ALL NIGHT swearing at what's SUPPOSED to be a usable operating system, maybe you'll be irritable too.

---

### Post by Therion on 2009-06-15
Well your attitude, swearing and sarcasm are certainly a rallying cry for my support.  

From what I can tell from you post's you did no prior research before installing Ubuntu (hence your boot-loader issues) and made no backups of your working installation.  And now, because Ubuntu doesn't fly on your machine out of the box, it's just crap?  Well I'm sorry it's not working out for YOU, personally, on system specs you obviously refuse to post for whatever reason, but Ubuntu is used by an awful lot of people with few or no problems which pretty much shoots down your over-generalizing arguments to the contrary.  Hate to tell you this, but your problems are, statistically speaking mind you, insignificant.  Doesn't mean we won't try to help you, but how about you help US, help YOU?

If you're serious about getting Ubuntu working on your machine, why don't you try using some polite language, maybe a few "please" and "thank you's" like your mother likely taught you? I think it says a lot about these forums that you've gotten as many polite responses as you have considering your woeful posting history here.

That or you're simply a troll...

---

### Post by Stugol on 2009-06-15
> **leandromartinez98 said:**
> Try installing Slackware in your other machine (the one with Windows).

I can only assume you're taking the piss. How on earth could installing an inferior version of linux on a different machine help me in ANY way?

---

### Post by leandromartinez98 on 2009-06-15
> **Stugol said:**
> I can only assume you're taking the piss. How on earth could installing an inferior version of linux on a different machine help me in ANY way?

For justice, I wouldn't say that Slackware is "a inferior version of Linux". There are many instances for which is a good alternative. And probably yes, I "was taking the piss", whatever that means.

---

### Post by raymondh on 2009-06-15
Let's start all over again Stugol ... post your machines' specs and go from there.

Also, when you get the chance ... read the release notes of your distro and the stickies' in the sub-forums.

---

### Post by Stugol on 2009-06-15
> **t0p said:**
> Or Debian.  You'd probably get on fine with Debian.

:p

Alternatively, you could reformat your hard drive and install some more Vista on the machine instead.  Windows 7 won't be much longer, perhaps you could install that.

Yeah, coz taking the piss will really help endear me to the way of the linux.

Look guys, I'm TRYING to use ubuntu. If I didn't give a damn, I'd just wipe it off and not bother posting.

> **t0p said:**
> It's strange how you have endless problems with Ubuntu when most of us don't.

Now THAT is crap. If having problems with Ubuntu was uncommon, there wouldn't be millions of desperate "help me! Linux has just EATEN my DOG!!" posts. Face it: Linux just LOVES to go wrong and force a user to go posting on a forum.

How many people have to post on a forum because their Windows won't work? Not many.

> **t0p said:**
>  If you wanted to persevere, and you stopped this "Linux is crap because I can't make it work" attitude, you'd find a lot of helpful folk in these forums.  Try us if you like.  Or don't.

I do want to persevere. That's why I'm here. And I'm not saying that Linux is crap because I can't make it work - I'm saying it's crap because it basically just BROKE ITSELF while updating. Wasn't anything to do with me at all!

If anyone wants to suggest some HELPFUL solutions, I'll be overjoyed to try them. But "try wiping it and reinstalling" or "try removing Windows completely, so you'll be completely screwed next time Ubuntu ***** a brick" isn't helpful.

---

### Post by leandromartinez98 on 2009-06-15
> **Stugol said:**
> 
Now THAT is crap. If having problems with Ubuntu was uncommon, there wouldn't be millions of desperate "help me! Linux has just EATEN my DOG!!" posts. Face it: Linux just LOVES to go wrong and force a user to go posting on a forum.


Yes, you discovered us. We are all hired by FORUM, the jeans company, and Linux has automatic breakeage stuff inside to promote the brand. 

Enough for me! See you.

---

### Post by c1rcu1t on 2009-06-15
I agree with Therion. I'm actually surprised that everyone who has responded has been so polite. I am a recent convert, and just like every other user I had problems with the transition to Ubuntu. There are issues to overcome initially, such as proprietary wireless cards, and printer setup, but once these issues are addressed, as frustrating as they might be, the beauty of the OS and of all open-source becomes obvious.

---

### Post by Stugol on 2009-06-15
> **Therion said:**
> From what I can tell from you post's you did no prior research before installing Ubuntu (hence your boot-loader issues) and made no backups of your working installation.

Backups? Working installation? I just installed the damn thing last night! And I've been up all night trying to get the damn thing to even WORK.

And as for the idea that I would need to do "research" before bunging a Live disc in and clicking "install", well, that's ridiculous. If I can install Windows, I can install Ubuntu off've a Live disc.

When something breaks, THEN I go looking for answers. Not before. Else I'd never get anything done.

> **Therion said:**
> 
And now, because Ubuntu doesn't fly on your machine out of the box, it's just crap?


No. Because Ubuntu just basically COMMITTED SUICIDE ALL BY ITSELF with its automatic updates. Weren't you listening?

> **Therion said:**
> Well I'm sorry it's not working out for YOU, personally, on system specs you obviously refuse to post for whatever reason,

I briefly described the system; and when asked for additional information, I said I would provide it tomorrow when I'm back in front of the system. What do you mean, I refuse to post them??

> **Therion said:**
> I think it says a lot about these forums that you've gotten as many polite responses as you have considering your woeful posting history here.


What posting history? This thread is my first post.

> **Therion said:**
> That or you're simply a troll...

No, I'm a disgruntled user of an operating system that seems to try its level best to break at every turn.

---

### Post by ZackM on 2009-06-15
You stated earlier in this thread that using an "outdated" version of Ubuntu was a ridiculous idea, since Jaunty wasn't a "beta" and that it should work just fine. However, look at your precious Windows and how every one of their systems start of crap, and then they make service packs to fix their mistakes. Let's see... Let's take a look at some of those.. ME, for example... Joke... Vista... Well, that's not even worth getting into. Even the famed XP had it's problems (still does) when it first came out, and I bet you were one of those people that couldn't figure that out as well. I understand getting mad because you run into troubles, however attacking the system for your ignorance isn't solving anything, nor is attacking anyone on these forums trying to help you.

---

### Post by Stugol on 2009-06-15
> **raymondhenson said:**
> Let's start all over again Stugol ... post your machines' specs and go from there

Certainly. When I'm back in front of the machine, I will do so.

---

### Post by Stugol on 2009-06-15
> **ZackM said:**
> You stated earlier in this thread that using an "outdated" version of Ubuntu was a ridiculous idea, since Jaunty wasn't a "beta" and that it should work just fine. However, look at your precious Windows and how every one of their systems start of crap, and then they make service packs to fix their mistakes. Let's see... Let's take a look at some of those.. ME, for example... Joke... Vista... Well, that's not even worth getting into. Even the famed XP had it's problems (still does) when it first came out, and I bet you were one of those people that couldn't figure that out as well. I understand getting mad because you run into troubles, however attacking the system for your ignorance isn't solving anything, nor is attacking anyone on these forums trying to help you.

I'm not attacking people on these forums who are trying to help me. In fact, as I recall I've been quite reasonable with people who are being helpful. People who offer stupid suggestions, however, like deleting my Windows installation or installing Slackware deserve no such respect.

Yes, granted, Windows isn't perfect either - especially new releases. However, they DO tend to load up, let you log in, work with your keyboard... that kind of thing. When has Windows EVER refused to talk to a mouse and keyboard?

Oh, and for the record, I tried plugging a PS/2 keyboard in. Ubuntu STILL refused to accept keystrokes. When has Windows ever done that?

---

### Post by overdrank on 2009-06-15
To Stugol, sorry for your troubles but you may start a new thread. State your issues in a calm manner.
To the community please keep the [COC]("http://ubuntuforums.org/index.php?page=policy") in mind.
> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.

---

