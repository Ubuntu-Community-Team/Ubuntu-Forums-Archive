---
title: "no You Tube videos"
date: 2012-05-28
forum: Desktop Environments
---

### Post by Autodave on 2012-05-28
I have installed Xubuntu on MANY machines and have gone through the "normal" amount of aggravavation getting You Tube videos to work.  However, this machine has me stumped.  I have installed the xubuntu-restricted-extras, tried Gnash instead of Flash, tried everything that I can think of, but still no good.  All I get is the black box w/nothing to click on.

This particular install was Xubuntu 11.04

Any help?

---

### Post by Peripheral Visionary on 2012-05-28
No error message at all? Might be a video driver issue.

I can offer some encouragement with Xubu 12.04 though. The new kernel and stuff in the latest restricted-extras package works out of the box on my 8-year-old Dell (Celeron processor, 512 RAM). Why not try Xubu 12.04 and enjoy 3 years of support?

---

### Post by Autodave on 2012-05-28
> **Peripheral Visionary said:**
> No error message at all? Might be a video driver issue.

I can offer some encouragement with Xubu 12.04 though. The new kernel and stuff in the latest restricted-extras package works out of the box on my 8-year-old Dell (Celeron processor, 512 RAM). Why not try Xubu 12.04 and enjoy 3 years of support?


I tried installing 12.04 prior, but it would say "unknown error" and boot me out of the installation.  I know that disc was good because I had installed it on another machine with no problems.

The machine I was trying to install it on is about 10 years old.  It is a 1.4 with one gig RAM and built on video.

---

### Post by Peripheral Visionary on 2012-05-28
Sometimes even with a good disk there's just a moment when something isn't read properly. I installed my Xubu from the LiveCD. First time, "unknown error." Minutes later using the same disk, full, effortless, flawless installation.  It's worth a shot.

---

### Post by Rodney9 on 2012-05-28
These two Firefox flash plug-ins have helped many on older machines

Low quality Flash

[https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/?src=api](https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/?src=api)

Flash Aid

[http://webgapps.org/add-ons/flash-aid/](http://webgapps.org/add-ons/flash-aid/)

Rodney

---

### Post by Autodave on 2012-05-30
> **Rodney9 said:**
> These two Firefox flash plug-ins have helped many on older machines

Low quality Flash

[https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/?src=api](https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/?src=api)

Flash Aid

[http://webgapps.org/add-ons/flash-aid/](http://webgapps.org/add-ons/flash-aid/)

Rodney

No good: tried them both.  I have Xubuntu 12.04 installed and running fine: except for You Tube.  All I get is a black box where the video should be.

I have installed the restricted extras and add-ons.  I have tried and then disabled Flashaid.

If I boot this machine from the install disc, I can watch You Tube with no problem at all.  But, once installed, nothing.  

What am I missing?

---

### Post by overcast on 2012-05-30
I have the same issue. If the gnash is the only flash plugin installed on firefox then I guess it shows similar issue. Are you seeing this on chrome or midori too?

---

### Post by Autodave on 2012-05-30
> **overcast said:**
> I have the same issue. If the gnash is the only flash plugin installed on firefox then I guess it shows similar issue. Are you seeing this on chrome or midori too?


I have not tried Chrome, but I did try it on Xubuntu 11.04 and it did not work.

---

### Post by Autodave on 2012-05-30
> **Autodave said:**
> I have not tried Chrome, but I did try it on Xubuntu 11.04 and it did not work.


I would like to know why the videos play when I boot the machine using the install disc, but not when I install the program?  They played GREAT while running 12.04 from the CD!  What is different?

---

### Post by Peripheral Visionary on 2012-05-31
> **Autodave said:**
> I would like to know why the videos play when I boot the machine using the install disc, but not when I install the program?  They played GREAT while running 12.04 from the CD!  What is different?

Wow, that is weird! The only way I know to find out is to explore the Xubu disk from a file manager, listing the files, and compare the list against the installed one.  Who has time for that!?

I hope someone can tell why the LiveCD works but the installed (and updated?) version does not. Perhaps one of the updates did something that disabled YouTube videos? Would it work installed from your LiveCD but *not updated*?

---

### Post by Autodave on 2012-05-31
> **Peripheral Visionary said:**
> Wow, that is weird! The only way I know to find out is to explore the Xubu disk from a file manager, listing the files, and compare the list against the installed one.  Who has time for that!?

I hope someone can tell why the LiveCD works but the installed (and updated?) version does not. Perhaps one of the updates did something that disabled YouTube videos? Would it work installed from your LiveCD but *not updated*?

No......it did not.  So, my next step was to install the restricted extras.  No good.  Then, restricted plug-ins.  No good.

I then d-led newest version of flash from Adobe site: no good.  Tried Gnash: no good.  Uninstalled Flash and Gnash and just re-installed Gnash: no good.

There are no proprietary drivers needed or found.

I am at a loss on this one: hope someone has an idea.

---

### Post by Autodave on 2012-06-01
> **Autodave said:**
> No......it did not.  So, my next step was to install the restricted extras.  No good.  Then, restricted plug-ins.  No good.

I then d-led newest version of flash from Adobe site: no good.  Tried Gnash: no good.  Uninstalled Flash and Gnash and just re-installed Gnash: no good.

There are no proprietary drivers needed or found.

I am at a loss on this one: hope someone has an idea.


Just an update.  Burned a new 12.04 disc from the original d-l and it worked fine.  Installed first disc on 2 machines successfully, failed 3 times on third machine, worked on fourth machine, though.

---

