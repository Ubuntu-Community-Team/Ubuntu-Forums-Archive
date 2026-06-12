---
title: "Dark Age of Camelot"
date: 2006-08-29
forum: Gaming &amp; Leisure
---

### Post by n00blar on 2006-08-29
Has anyone been able to install and play this game under the latest wine and Ubuntu?

Upon running the update I get the following message:

This client cannot update your Dark Age of Camelot installation because a large number of key files are missing or corrupted.

I've searched around and no one seems to have a fix for this message. I looked at TransGaming and for them it appears to run fine, but I also found some people having issues even with TransGaming. I used to pay for their serivces, but I that company left me with a sour taste when I used to be their customer.

On the other hand World of Warcraft runs beautifully!! :KS

---

### Post by buntunub on 2007-06-30
DaoC now searches for a "My Games" folder, or somesuch moronic Windows thing. They put those changes in after Vista came out because Vista broke everyones install with all that new "security" crap they put in. You will have to do some tweaking with winecfg and probably install some additional folders in the /.wine tree to get the updater to work properly, I also suspect it checks for .dll's and if it doesnt fine the right ones, it most likely will spit that error out.

---

