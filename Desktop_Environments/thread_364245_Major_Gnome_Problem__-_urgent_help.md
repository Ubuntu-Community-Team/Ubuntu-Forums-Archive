---
title: "Major Gnome Problem  - urgent help"
date: 2007-02-18
forum: Desktop Environments
---

### Post by benndamann33 on 2007-02-18
Hi All,
I think my problem might have been manually installing a new version of perl, although I can't think of why that'd be so devistating. What I do no is now if I restart my computer I can only easily log in to kde, gnome takes literally 15-20 minutes to open after the login screen. Firsty it's just the human(tannish) background with a missing white rectangle taking up about the upper left corner. This lasts for a long time until gnome loads with an error message  i don't know verbatim but the essence is the gnome-settings  daemon failed to initialize. This sucks for serveral reasons
1. I can't seem to get into matlab at all(license manager will not load)
2. I can only used KDE which if I may add sucks
3. waiting 20 minutes for gnome also sucks

If I can whipe out gnome and restart that'd be awesome but I dont' want to lose any of my files...any suggestions?

fyi I'm using edgy eft and recently manually installed perl-5.8.8


ben

---

### Post by benndamann33 on 2007-02-18
nothing?

---

### Post by dreamsayer on 2007-03-15
> **benndamann33 said:**
> Hi All,
I think my problem might have been manually installing a new version of perl, although I can't think of why that'd be so devistating. What I do no is now if I restart my computer I can only easily log in to kde, gnome takes literally 15-20 minutes to open after the login screen. Firsty it's just the human(tannish) background with a missing white rectangle taking up about the upper left corner. This lasts for a long time until gnome loads with an error message  i don't know verbatim but the essence is the gnome-settings  daemon failed to initialize. This sucks for serveral reasons
1. I can't seem to get into matlab at all(license manager will not load)
2. I can only used KDE which if I may add sucks
3. waiting 20 minutes for gnome also sucks

If I can whipe out gnome and restart that'd be awesome but I dont' want to lose any of my files...any suggestions?

fyi I'm using edgy eft and recently manually installed perl-5.8.8


ben

I had this same problem today. I searched the forums and the net high and low, and tried all of the suggestions mentioned. Nothing worked. Typing gnome-settings-daemon in a terminal gave me a clue. There were a bunch of error messages re: label foregrounds and backgrounds.

So I logged into KDE and selected System Settings & in the Look & Feel section for Appearance, Desktop,Splash Screen & Window behavior I set all of the options contained to their defaults. I logged out of KDE and back into Gnome and Wallah!

I just happened to add KDE to my working Ubuntu system last night. I wanted to try something different. I suspect that the kpersonalizer that runs at first start may have caused this? Just a guess. I re-ran it and was playing around with the different themes. And this was after I successfully logged back and forth between Gnome and KDE without this problem.

---

