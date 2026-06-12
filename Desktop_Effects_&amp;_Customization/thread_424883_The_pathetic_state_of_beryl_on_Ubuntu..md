---
title: "The pathetic state of beryl on Ubuntu."
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by Xamindar on 2007-04-27
Please don't take offense to anyone who is on the Ubuntu beryl team but I recently came from gentoo where I had Beryl running wonderfully on my computer.  It used to rarely crash and I was quite happy with it.

But the beryl on Ubuntu constantly goes "white" and I have to restart Xgl to get it back.  I NEVER had the white screen problem on Gentoo.  What is going on here?  Is there something I have forgotten to do?  I can't imagine what.  And yes, I know it is alpha software but this white screen issue and a few other instabilities have been here ever sense I first installed Feisty beta.  Whoever is in charge of the beryl packages is not doing what they are supposed to be doing.  I know others are having this problem as well, I have seen their posts in the forums.  It also seems like an xgl only problem at this time.  So I am specifically asking:  Why isn't anyone fixing these packages?  Beryl worked back on Gentoo so it's not a hardware problem.  Do I have to end up compiling them myself?  Someone needs to be kicked out if they are not going to bother listening to the complaints about these issues from so many people having them.

I am sorry if I sound harsh, it is frustrating that the ubuntu beryl people don't care.

---

### Post by gatiba on 2007-04-27
Have you installed Nvidia drivers from [www.nvidia.com?](www.nvidia.com?)
If so reinstall them... It solved my white screen's problem...

---

### Post by cogadh on 2007-04-27
Beryl works fine on Ubuntu, you just need to have the right system config first. I followed the instruction here: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) to the letter and it works perfectly. Well, almost perfectly. I still have a problem with resizing windows, but all of the Beryl features work amazing.

---

### Post by Aetherius on 2007-04-27
Why are you using XGL whenever AIGLX tends to much faster and stable..er? Especially since aiglx is there by default if you've got ur nvidia blobs.

---

### Post by kpolice on 2007-04-27
I don't know where you guys read that he is using an nvidia card :confused: 

XGL is the best we ATi users have for Radeon 9500+ cards.

---

### Post by guitarist on 2007-04-27
> **kpolice said:**
> I don't know where you guys read that he is using an nvidia card :confused: 

XGL is the best we ATi users have for Radeon 9500+ cards.


That's not necessarily true.  I've been using AIGLX with my X600 Mobility for months.  It's not quite as fast as XGL (because you have to use the open source radeon driver), but its FAR more stable. 

Admittedly other 3d apps don't really work (because of the radeon driver) but if I really want to game/etc, I go to an OS that actually supports such things.  For a daily desktop with much more usability (desktop wall + scale + tabbed windows = MUCH more useful desktop) and prettier appearance, though, (K)ubuntu + Beryl = one of the best solutions out there.

And if he's using XGL, you can almost bet he's NOT using an Nvidia card, because Nvidia drivers support AIGLX with actual 3D acceleration in other programs too (what a thought, eh, ATI?).

---

### Post by kpolice on 2007-04-27
AIGLX is not as fast and in my case leave a lot of artifacts in the screen. 

XGL is stable as a rock in my case, I'm not using Ubuntu, but everyone has a different experience.

---

### Post by fwojciec on 2007-04-27
ZERO problems with Beryl and Feisty on my computer - I'm using geforce 7900GS card, nvidia-glx-new driver and I've followed the howto on beryl-project wiki page.

---

### Post by TheCleaner on 2007-04-27
I had the "white" problems when I first upgraded to Feisty.  Found out that the latest version of Beryl didn't play nice and had to downgrade one version...after that all was fine.

---

### Post by theredcross on 2007-04-27
> **Xamindar said:**
> I am sorry if I sound harsh, it is frustrating that the ubuntu beryl people don't care.

It amuses me to no end that you think the problem exists because the dev team doesn't care.

---

### Post by Xamindar on 2007-04-27
> **guitarist said:**
> That's not necessarily true.  I've been using AIGLX with my X600 Mobility for months.  It's not quite as fast as XGL (because you have to use the open source radeon driver), but its FAR more stable. 

And if he's using XGL, you can almost bet he's NOT using an Nvidia card, because Nvidia drivers support AIGLX with actual 3D acceleration in other programs too (what a thought, eh, ATI?).

Sorry, I failed to mention the video card.  I have a radeon x1400 on this laptop.  If I would have waited until now to buy this laptop then I could have gotten an nvidia card, oh well.  guitarist, please tell me how you are using the open source drivers.  Everywhere I read tells me it doesn't work on my card.  Should I try it and just see if it works?  If it is a little slower that is acceptable if the crashes and white screens go away.

> **kpolice said:**
> AIGLX is not as fast and in my case leave a lot of artifacts in the screen. 

XGL is stable as a rock in my case, I'm not using Ubuntu, but everyone has a different experience.

That's what I was used to from xgl under Gentoo.  Not the case in Ubuntu.

> **theredcross said:**
> It amuses me to no end that you think the problem exists because the dev team doesn't care.

How does that amuse you?  It seems pretty obvious to me when they have decided not to provide an xgl binary any more for us forced xgl users.  It can't be that hard to provide it.

---

### Post by cogadh on 2007-04-27
I could be wrong, but there is an XGL driver available through the repositories "xserver-xgl". It is in the universe repository, but it is defintely available for Ubuntu.

Also, which version of Beryl are you using? I've read several reports that there is a problem with the latest Beryl and the ATI drivers.

---

