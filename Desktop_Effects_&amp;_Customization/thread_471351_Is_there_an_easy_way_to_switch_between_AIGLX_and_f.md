---
title: "Is there an easy way to switch between AIGLX and flgrx for ATI card?"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by BeardlessForeigner on 2007-06-11
I installed feisty right when it came out, my first experience with linux. At first I had Beryl running with flgrx and XGL. However, I was having a couple problems. My video playback suffered under XGL, games like WoP and Tremulous had problems with in game text showing up right, and my computer crashed fairly often. So I ended up reinstalling feisty and enabling AIGLX when I learned you could do this, and all of the above problems went away. Beryl runs better now and I can even play WoP. 
     However, it seems like some games like Frets on Fire require flgrx, and WoP might run better with it (maybe my problems b4 were just with XGL?). I'd like to be able to just turn off Beryl and use the propreitary driver for FoF for instance, either by switching off in Restricted Drivers Manager or having a seperate session or something. Does anyone have any experience with this? I think installing flgrx requires disabling AIGLX in X.org and possible makes other changes to X.org, and I have a problem uninstalling it cleanly b4 and just reinstalled feisty, so I'm not too hopeful but figured I'd ask if anyone else had any thoughts.

---

### Post by BeardlessForeigner on 2007-06-12
As a thought on this, to get Beryl working with AIGLX I merely had to change some lines in Xorg.conf. Since I believe using flgrx consists of first installing it, and then either manually or automatically configuring Xorg.conf to use it, is there some way to have one session using one Xorg.conf file for general use and one session using another enabling flgrx for gaming?

---

### Post by kpolice on 2007-06-12
You can setup an XGL session and a non-XGL session so all you had to do is logout and change your session. 

How did you setup Beryl?

---

### Post by BeardlessForeigner on 2007-06-12
> **kpolice said:**
> You can setup an XGL session and a non-XGL session so all you had to do is logout and change your session. 

How did you setup Beryl?

I set up Beryl according to this guide: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon). The first time i set up Beryl with XGL according to the method on ubuntuguide. From that I know I can have an XGL and non XGL session. But the question is can I have each session use a different Xorg configuration file? Also, I dont want XGL at all if I dont need it since it game me problems. Id like one session with open source radeon driver and AIGLX and one with flgrx.

---

