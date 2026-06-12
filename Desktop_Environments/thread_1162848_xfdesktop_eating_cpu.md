---
title: "xfdesktop eating cpu?"
date: 2009-05-18
forum: Desktop Environments
---

### Post by moore.bryan on 2009-05-18
is anyone else having this problem? for about two days now, xfdesktop takes forever to load (3-5 minutes) and then eats cpu (100%) for about ten minutes. any ideas where i can start debugging this?

---

### Post by Lampi on 2009-05-18
try to find out what application is causing this:

enter "top" in terminal and observe ... the one you are looking for is taking the most and highest cpu time, so it stays on the first row most of the time.

---

### Post by kerry_s on 2009-05-18
have you checked your ~/.xsession-errors

just had a thought is xfce4-settings-helper running?

---

### Post by moore.bryan on 2009-05-18
> **Lampi said:**
> try to find out what application is causing this:

enter "top" in terminal and observe ... the one you are looking for is taking the most and highest cpu time, so it stays on the first row most of the time.
yup, first thing i did... "xfdesktop" is hogging all the memory.
> **kerry_s said:**
> have you checked your ~/.xsession-errors

just had a thought is xfce4-settings-helper running?
never even thought of checking ~/.xsession-errors! i'll have to check that when i get home from work. i think i have xfce4-settings-helper disabled at startup; why, is that a known issue?

---

### Post by kerry_s on 2009-05-18
> i think i have xfce4-settings-helper disabled at startup; why, is that a known issue?

hmm, funny thing mines unchecked to, but it is running in session.
i don't think it matters but i'm running debian xfce4, not xubuntu.

---

### Post by moore.bryan on 2009-05-18
the truly funny thing is i'm also not running xubuntu, but debian squeeze with xfce 4.6.1! :-)

i simply posted in both forums because i seem to get better answers here!

---

### Post by kerry_s on 2009-05-18
> **moore.bryan said:**
> the truly funny thing is i'm also not running xubuntu, but debian squeeze with xfce 4.6.1! :-)

i simply posted in both forums because i seem to get better answers here!

then help you will get my friend, cause were on the same page. :D
also if you change "squeeze" to "testing" you'll have a true rolling release.

---

### Post by moore.bryan on 2009-05-18
isn't squeeze the same thing as testing? i'm still having the xfdeskop hogging issue. :-(
many thanks for the help!

also, can anyone explain why i have five or more xfdesktops listed by top at all times?

---

### Post by kerry_s on 2009-05-18
> **moore.bryan said:**
> isn't squeeze the same thing as testing? i'm still having the xfdeskop hogging issue. :-(
many thanks for the help!

yes, it is but squeeze will eventually become stable, when that happens you will eventually be running stable, if you use testing it will always be testing no matter what the next name is. that's the idea of a rolling release, just install once and update from then on. not a big thing you got years to think about it.

for the hogging issue, what i would do is change to the failsafe terminal at the log in screen, remove the .xfce4 folder, uninstall xfdesktop completely, then reinstall it. see if that helps.

are you running any effects?

---

### Post by moore.bryan on 2009-05-19
> **kerry_s said:**
> yes, it is but squeeze will eventually become stable, when that happens you will eventually be running stable, if you use testing it will always be testing no matter what the next name is. that's the idea of a rolling release, just install once and update from then on. not a big thing you got years to think about it.

for the hogging issue, what i would do is change to the failsafe terminal at the log in screen, remove the .xfce4 folder, uninstall xfdesktop completely, then reinstall it. see if that helps.

are you running any effects?

ah, that makes sense. i don't have my sources set for squeeze, as it turns-out; instead, they're set as testing.

i'll try your suggestion... my ~/.xsession-errors file looked pretty screwy to me; i've put it [here]("http://www.bmoore.net/xsession-errors.txt") for anyone's perusal.

---

### Post by kerry_s on 2009-05-19
holly crap, if the reinstall of xfdesktop don't work i would try a complete reinstall, it looks like a goofy install, could be something didn't setup right.

if you do reinstall, try the expert install mode in advanced section, you can get a more targeted install, get a choice of sudo system, there's also the option for grub2.

---

### Post by kerry_s on 2009-05-19
oh fudge, looks like i'll be reinstalling to, that drive gave out.
got the good ol "no disk found" or something like that. ahhh
it's a roll of the dice when you buy used, luckly i got 6 try's in this bundle, bought 6 used drives $10. ;)

---

### Post by moore.bryan on 2009-05-19
> **kerry_s said:**
> holly crap, if the reinstall of xfdesktop don't work i would try a complete reinstall, it looks like a goofy install, could be something didn't setup right.

if you do reinstall, try the expert install mode in advanced section, you can get a more targeted install, get a choice of sudo system, there's also the option for grub2.
it would be strange if a complete reinstall would be necessary; this isn't a problem i've had SINCE install, just recently.
> **kerry_s said:**
> oh fudge, looks like i'll be reinstalling to, that drive gave out.
got the good ol "no disk found" or something like that. ahhh
it's a roll of the dice when you buy used, luckly i got 6 try's in this bundle, bought 6 used drives $10. ;)
i guess a purge every now and again is healthy. ;-)

---

### Post by kerry_s on 2009-05-19
> i guess a purge every now and again is healthy. 

i'm just now getting things setup, but i'm back up and running, just need to install all the other programs, since i started from the base, i've only added the basics so far.

> it would be strange if a complete reinstall would be necessary; this isn't a problem i've had SINCE install, just recently.

you never know, time does funny things. perhaps checking your synaptic logs for the dates when the problem started, might be some update you can try reinstalling.

---

### Post by moore.bryan on 2009-05-19
true... i think i'll do that when i get home today. i'll keep the forum posted.

---

### Post by kerry_s on 2009-05-19
> **moore.bryan said:**
> true... i think i'll do that when i get home today. i'll keep the forum posted.

i think that's the best solution. my installs have been clean, the .xsession-errors is very minimal, compared to yours.

this time i decided not to use the mixer applet and do my own, don't like that new mixer.

---

### Post by moore.bryan on 2009-05-20
wow, no love from arch or debian. when i reinstalled debian, i couldn't get an xserver to start for the life of me... even ran lspci to make sure i had the right address. i DID NOT have this problem on my first install from the exact same cd. STRANGE. so, i thought i'd throw-in my arch linux ppc disc and see if that had any better luck. running FROM THE CD, it told me the cd was unmountable and unable to install any packages. WEIRD. what in the world could cause all these "issues?"

---

### Post by kerry_s on 2009-05-20
sounds like you got hardware issues to me, if i had to guess i would check the ram first, you have all the signs. try running the memtest in the cd boot options.

---

### Post by moore.bryan on 2009-05-20
ram's relatively new and tested fine. :-(

---

### Post by kerry_s on 2009-05-20
> **moore.bryan said:**
> ram's relatively new and tested fine. :-(

i don't know then, try googling your mac version for similar problems.

---

### Post by moore.bryan on 2009-05-20
unfortunately, no dice through a search. i must be missing something silly... must have selected something awkwardly. dedicated to solving this tonight, though!

---

### Post by kerry_s on 2009-05-20
> **moore.bryan said:**
> unfortunately, no dice through a search. i must be missing something silly... must have selected something awkwardly. dedicated to solving this tonight, though!

hmm, whats the model computer? i do a lot of computers for friends, i might know someone with the same model i could ask.

---

### Post by moore.bryan on 2009-05-20
thankfully, it was simply my own stupid fault; i forgot to add "video=ofonly" at the install line for debian, along with "desktop=xfce." silly, silly... running on it right now, in fact!  thanks for all the help. now if i can only remember how i got sound to work last time...  ;-)

---

### Post by kerry_s on 2009-05-20
> **moore.bryan said:**
> thankfully, it was simply my own stupid fault; i forgot to add "video=ofonly" at the install line for debian, along with "desktop=xfce." silly, silly... running on it right now, in fact!  thanks for all the help. now if i can only remember how i got sound to work last time...  ;-)

yeah, you got remember special options, write it down! lol
luckly for me the only thing i add is "vga=791".


> along with "desktop=xfce."

thats in the advanced options now, its something like advanced> alternate desktops, select xfce4> install, press <tab> to add your boot lines and enter. the new net installer lets you select from all 4 desktops.

i still prefer custom, i use advanced> expert install.

---

### Post by moore.bryan on 2009-05-21
yeah, i stay in the non-advanced options on the ppc; just seem to work better so long as i remember the options i need!

it still frustrates me, though, i wasn't able to figure-out the original xfdesktop problem. the answer shouldn't have been a clean reinstall.

---

### Post by kerry_s on 2009-05-21
> **moore.bryan said:**
> yeah, i stay in the non-advanced options on the ppc; just seem to work better so long as i remember the options i need!

it still frustrates me, though, i wasn't able to figure-out the original xfdesktop problem. the answer shouldn't have been a clean reinstall.

yeah, i know, reinstall is the simple solution. with me, i mess with a lot of stuff and it's sometimes a while to find out i broke something, then to try and remember what i messed with. i've learned to start over a lot. ;)

---

### Post by redwingsfan13 on 2009-05-21
I am running xubuntu 9.04 and I had the exact same problem before. It's some kind of bug with XFCE or something. The solution I found is to do this: [https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616)
After I did this, everything worked fine.

---

### Post by moore.bryan on 2009-05-22
> **redwingsfan13 said:**
> I am running xubuntu 9.04 and I had the exact same problem before. It's some kind of bug with XFCE or something. The solution I found is to do this: [https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616)
After I did this, everything worked fine.

interesting bug read, @redwingsfan13... already reinstalled, but this could prove INCREDIBLY helpful in the future if the bug pops back-up. i am a little interested in why launchpad didn't decide to split the bug into two since the trash and xfdesktop problems seem unrelated, as some of those affected have one and not the other... like me.

on a completely unrelated side-note, your wings barely pulled-out the win the other night with the 'hawks outplaying them the entire game. have you solved the "'bulin wall?" ;-)

---

