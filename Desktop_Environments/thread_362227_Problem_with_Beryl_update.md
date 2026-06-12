---
title: "Problem with Beryl update"
date: 2007-02-15
forum: Desktop Environments
---

### Post by brainyron on 2007-02-15
I ran the Beryl update this morning and ever since then, my skydome has been messed up.  My skydome image isn't drawn.  In fact, the colors that are selected in my settings manager aren't even shown, it's just black.  With the image enabled, the cube smears across the skydome and it doesn't go away until I zoom back in on the cube.  With the image disabled, I can rotate the cube without smearing but it's still just flat black. Everything else seems to be working so far.

Any suggestions as to what I could do to get my skydome working again or am I just screwed?

I'm running on a Mobility Radeon 9700 with AIGLX, as installed by the script that I found here:  [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)

---

### Post by louis_nichols on 2007-02-15
This is because the script installs beryl from svn, which is basically experimental and it is expected to not behave very well.

There's not muvh you can do about it, other than wait for a new update, which will hopefully fix the problem. Updates to Beryl are sometimes daily, so you shouldn't have to wait long.

Another option is to downgrade the version for now. You can do this in synaptic with the force-version option, I think.

---

### Post by PriceChild on 2007-02-15
I strongly recommend you remove the trev repo in your sources list, add```
deb http://ubuntu.beryl-project.org edgy main
```And force all the beryl packages down to 0.1.9999.2~0beryl1

---

### Post by Waappu on 2007-02-15
> **PriceChild said:**
> I strongly recommend you remove the trev repo in your sources list, add```
deb http://ubuntu.beryl-project.org edgy main
```And force all the beryl packages down to 0.1.9999.2~0beryl1

Hi

Could you please explain why so maybe I should change that script?
I have used SVN repos without problems. 

Also it seems to me that updates from repo you recoment cause also problems to some users.

---

### Post by PriceChild on 2007-02-16
> **Waappu said:**
> Hi

Could you please explain why so maybe I should change that script?
I have used SVN repos without problems. SVN is for developers and bug testers. Those that expect things to break, want to find out why and how they're breaking, then give detailed reports and/or fix them.

> **Waappu said:**
>  Also it seems to me that updates from repo you recoment cause also problems to some users.I'm not saying that the "official stable" beryl repos have been completely stable, however they're a lot more stable than SVN. There are work arounds for almost all of the problems people are suffering and most importantly... We will support them!

If you are running svn and then ask for help here, the beryl forums or on irc then we don't have a clue what revision you are on, what the developers are working on at that point and whether they've done things on purpose... you're effectively on your own.

I advise you to downgrade to "stable".

---

### Post by Waappu on 2007-02-16
> **PriceChild said:**
> SVN is for developers and bug testers. Those that expect things to break, want to find out why and how they're breaking, then give detailed reports and/or fix them.

I'm not saying that the "official stable" beryl repos have been completely stable, however they're a lot more stable than SVN. There are work arounds for almost all of the problems people are suffering and most importantly... We will support them!

If you are running svn and then ask for help here, the beryl forums or on irc then we don't have a clue what revision you are on, what the developers are working on at that point and whether they've done things on purpose... you're effectively on your own.

I advise you to downgrade to "stable".

Hi

Thanks for explaining.
I will change that scrip to use official repository or make possibility to choose SVN

---

