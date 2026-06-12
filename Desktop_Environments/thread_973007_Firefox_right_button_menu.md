---
title: "Firefox right button menu"
date: 2008-11-06
forum: Desktop Environments
---

### Post by secdroid on 2008-11-06
Hope this is an appropriate place to ask.  If not, please point me.

Firefox 3.03 (on 8.10) -- right button menu does not always come up with right mouse click on URL.  I get the menu most times, but some clicks result in going immediately to a selection from the menu.  (E.g., go directly to "Bookmark this Link" or "Copy Link Location" _actions_ rather than menu.)  No problems with left button.

I don't notice any mouse issues with other apps, but I use right click far, far more often in Firefox than in all other apps combined.

I noticed the same behavior on the same box with 3.03 on 8.04.1, but not with Dapper/1.5.  

Don't have another PS/2 mouse to compare.  No other distros on box at the moment.

Googled, but didn't spot others with this problem.  Bad mouse, Firefox issue, or are there tweaks that might help?

---

### Post by boterbram on 2008-11-19
Same error here, it seems to happen more often when the button is not pressed very well, like when you press on the side of it instead of the middle. Also it happens more often when the button is pressed very quickly. Any ideas? I myself think it could have something to do with the signals coming from the mouse which are not processed correctly?

---

### Post by secdroid on 2008-12-01
> **boterbram said:**
> Also it happens more often when the button is pressed very quickly.
If I hover the mouse pointer over a hyperlink for a few seconds before right-clicking, I always get the full menu.  If I right-click _immediately_ after positioning the mouse pointer, I often get undesired actions (instead of the menu).

Thus, it seems to be a Firefox timing issue.  No other application shows this problem.  This would appear to clear the hardware.

Even though I have a slow CPU (900 MHz Duron/1.5 GB), the Processor display is not usually showing significant CPU usage.  Memory usage does not appear to be an issue.

However, I did not see this problem with 8.04.1 & Firefox 3.0x, using the same processor.

I clear most private data when exiting, so my cache sizes are relatively small.

Suggestions?

---

### Post by secdroid on 2008-12-01
boterbram: Something you might want to try --

I was going to test restoring preferences to defaults & disabling all add-ons to see if I could improve the situation.  It appears that I stumbled across a solution/work around.

Edit->Preferences->Privacy->Private Data [Always Clear Private Data] checkbox was checked, as I had it in 8.04.1.  The [Ask Me...] check box was also checked, also as with 8.04.1.

It seemed to me that this mechanism worked much more slowly in 8.10 than 8.04.1.  Specifically, there was a long interval between when I exited FF and when the data clearing permission dialog box popped up, as well as a long interval bwtween when I allowed the permission dialog to start clearing and when the FF processes finished.  This part of FF "felt" slower than 8.04.1.  (No way to measure now.)

So, I turned off the automatic clear options and tried to get the right-click actions to fail on a hyperlink.  _Could not get it to fail_.

Never got around to disabling any add-ons.  The only thing I changed was the private data clearing options.

FWIW, FF "feels" faster now.  Change in storage model since FF 3.0 in 8.04.1?  Only affects those of us with slower systems?  I don't know...

Running Ubuntu (Gnome) -- Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.4) Gecko/2008111318 Ubuntu/8.10 (intrepid) Firefox/3.0.4

---

### Post by secdroid on 2008-12-02
After 23 hours, I'd say that the improvement has been substantial, but not 100% perfect.  With lots of other things going on (e.g, torrent, internet radio, etc.) I get the _very occasional_ glitch.  Nothing like before.

This is probably the last I will post about this. 

Gnome keeps getting bigger & slower.  Mono keeps encroaching, whether we want it or not.  KDE 4.x is slow and problematic and Xubuntu is a fairly slow version of XFCE.  I think 8.04.1 was the last [U,Ku,Xu]buntu that was acceptable (to me) on a 900 MHz Duron, regardless of memory.

I'm going to do a command line install of 8.10 and then install LXDE.  I tried it as an alternative login via GDM and was very impressed.  It will be even nicer without all of the other bloat.  Time to clean house.

[http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde]("http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde")
[http://wiki.lxde.org/en/Ubuntu]("http://wiki.lxde.org/en/Ubuntu")
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop")

---

### Post by scrapee on 2009-01-05
I had the same problem, I disabled the "Ask me before clearing private data" checkbox and the problem was gone. The "Always clear private data ..." checkbox was not checked. 

I have a Intel Core Duo with 1.66 GHz and 4 GB Ram so I don't think that is is a performance issue.

Thx for the tip

---

### Post by dodle on 2009-01-21
I've had this problem for a long time with 8.04 and haven't heard of a solution yet.

> **scrapee said:**
> ...I disabled the "Ask me before clearing private data" checkbox and the problem was gone. The "Always clear private data ..." checkbox was not checked. 

Thanks for the suggestion, but it didn't work for me.  The only solution that I've found is: Hold down the right mouse button until the menu appears, instead of just "clicking" it quickly.

---

### Post by scrapee on 2009-01-22
I also installed the Mouse Gesture Extension for Firefox. It changes sequence in which the menu is drawn. Normally the Menu is drawn when you press the right mouse button. With the Extension the Menu is drawn when you release the right mouse button. This completely solved the issue for me

[http://www.mousegestures.org/](http://www.mousegestures.org/)

---

