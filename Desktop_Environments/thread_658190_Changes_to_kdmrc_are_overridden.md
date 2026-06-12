---
title: "Changes to kdmrc are overridden?"
date: 2008-01-04
forum: Desktop Environments
---

### Post by suhaib on 2008-01-04
Hi,

I recently had to rebuild my system, so I chose to install the Ubuntu Gutsy 7.10 command line only.  Then ontop of this, for my GUI I chose to install the package kde through apt (bear in mind that I installed the KDE package and not kubuntu-desktop).  Everything seemed to have gone fine, had to configure some programs and settings but all is good.  I did notice a problem however, and I've tried to research and resolve the matter but so far I have been unsuccessful.

When I boot up my Ubuntu/Kubuntu whichever term would be more correct in this instance, I noticed that KDE looked uglier than it should.  I checked the control centre/system settings and under appearance i checked to make sure that the desired theme and icon set was installed, this was the case.  However, i noticed that despite this, I'm pretty certain that some elements of my themes are being overridden, but i don't know how and where i can adjust this.  For example, the progress bar is just a flat bar which has the same colour as my windows (so in reality it barely depicts any progress lol)...  Certainly not how it should look on the plastik theme!  In addition to this, some buttons have also been overridden.

Despite that, I only found out that this was the case after trying to install some kdm themes; the default one is really plain and needs to go, however it doesnt want to go, even after specifying a new theme and modifying the kdmrc file in /etc/defaults/kdm it doesn't budge.

I was hoping that someone out there on these forums has installed kde through similar means, or simply has some suggestions or a solution.

Thanks!

---

### Post by suhaib on 2008-01-07
BUMP! 

The  kdm themes are now working, but the icons and other elements mentioned above are not.

---

