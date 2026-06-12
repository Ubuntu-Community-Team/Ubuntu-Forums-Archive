---
title: "Effects not working"
date: 2009-10-07
forum: Desktop Environments
---

### Post by StolenPie on 2009-10-07
> **Bill.the.noob said:**
> Hey there all. I enjoy all posts on this thread. I'm finding this forum very helpful as I'm a greenhorn to linux. My  predicament is this. I have recently installed compiz on my desktop {Ubuntu 9,04} and everything works great except for the animations . I can't seem to get any of them working after hours of messing around. Anyone else come across the samething. I really like the flaming windows when they close, but right now i have to hold my lighter up to the screen to get a similar but crappy effect.     I found a similar problem on another thread by Phantom Hoover " Compiz not working" I'm going to try their solution and see how far I get. Thanks                                                                               Sorry peeps . No such luck. Must be a conflict issue. I might as well uninstall it . The novelty of it is starting to wear off a bit. Later!

I'm in a similar situation, everything from compiz seems to be working, except the animations. I'm not quite as willing to uninstall, however. Can anyone offer any help? I read thru this whole thread, couldn't find an answer.

---

### Post by mo0nykit on 2009-10-08
**@StolenPie** and **@Bill.the.noob**

Have you installed **compizconfig-settings-manager**?```
sudo apt-get install compizconfig-settings-manager
```After that, look in System --> Preferences --> Compiz Settings Manager
Settings for all other compiz extras are there :) You have to manually install the settings manager since it doesn't ship with Ubuntu by default.

---

### Post by hariks0 on 2009-10-08
> **StolenPie said:**
> I'm in a similar situation, everything from compiz seems to be working, except the animations. I'm not quite as willing to uninstall, however. Can anyone offer any help? I read thru this whole thread, couldn't find an answer.

If they are visible but not working, I don't know what to do. [Try changing the visual effects to "Extra" in Appearance.]

But if they have recently disappeared, there is a workaround which helped me. It is the compiz-fusion-plugins-extra that makes the mess. The latest version available as per Synaptic is 0.8.2-0ubuntu1.2 (ppa.launchpad.net) I forced it to install/retain the package with version 0.8.2-0ubuntu1 (jaunty). Now all the effects and animation add-on are back in my ccsm.

Hope it helps.

---

### Post by overdrank on 2009-10-08
Hi and I have moved your post and the responses from The Great Desktop Effects FAQ of 2009 as it is not for support questions. :)

---

### Post by StolenPie on 2009-10-09
I tried switching to Extra effects... all that did was disable everything else that Compiz was doing, so I had to put it all back again. It seems that whatever program was managing the effects before I installed the ccsm (@mo0nykit, yes I have the ccsm installed) simply isn't being overridden by Compiz. Maybe someone knows what that is, and where I might be able to switch it off?

---

### Post by dustbindiva on 2009-10-09
I had the darndest time trying to get my visual effects back. The extra effects feature was dimmed out. I re-installed the Compiz packets but that did not help. I finally found a website where I could install the Hardy version for me in 8.04 you can take a look around that site for your 9.04 version

[http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/)

---

### Post by StolenPie on 2009-10-09
Thanks, but it's not the problem that they were there and then disappeared. The lamp icon is there, it's not greyed out. I can select all the effects I like, but none of them actually DO anything.

---

### Post by mo0nykit on 2009-10-10
Hmmm :-k If the Extra visual effects is grayed out, how about reinstalling your video drivers?

---

### Post by StolenPie on 2009-10-17
it's not greyed out... but how would I install video drivers? According to System > Hardware Drivers I don't have any.

Edit: I'm thinking, it might be because I have an Intel Graphics card, even though it's not blacklisted. Looks like I'm not gonna make any progress here.

---

