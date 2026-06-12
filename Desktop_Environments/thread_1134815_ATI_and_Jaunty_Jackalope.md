---
title: "ATI and Jaunty Jackalope"
date: 2009-04-24
forum: Desktop Environments
---

### Post by SDL486 on 2009-04-24
I have a Dell Inspiron 600m with an ATI Radeon 9000 card.  I just did a clean install of Jaunty and when I minimize or maximize a window it lags and the menus will lag occasionally.  For example when I maximize a window from the panel it lags by a second and when I click on firefox lets say after opening the applications menu it lags and the animation is slow.  Is there a bug or fix for this?

---

### Post by LT1Caprice57L on 2009-04-24
> **SDL486 said:**
> I have a Dell Inspiron 600m with an ATI Radeon 9000 card.  I just did a clean install of Jaunty and when I minimize or maximize a window it lags and the menus will lag occasionally.  For example when I maximize a window from the panel it lags by a second and when I click on firefox lets say after opening the applications menu it lags and the animation is slow.  Is there a bug or fix for this?

Same computer, same problem, replied to a couple other threads concerning it, no dice.  Seems we're some of the unlucky folks with adapters that ATI decided to stop supporting.  Perhaps you should shoot ATI an email or give 'em a call and let them know you're disappointed.

...in the mean time, I'm going back to Intrepid. *sigh*

---

### Post by SDL486 on 2009-04-24
Unfortunately I think I might revert back to 8.10 also.  Do you have any clue as to what the problem is?

---

### Post by krazyd on 2009-04-24
Try this, and let us know how it goes:
[http://ubuntuforums.org/showthread.php?p=7027741#post7027741](http://ubuntuforums.org/showthread.php?p=7027741#post7027741)

---

### Post by SDL486 on 2009-04-24
Thanks I'll try this later!

---

### Post by JK3mp on 2009-04-24
Yeah the 9000 series i think in general are all unsupported in the new catalyst drivers. I had an ATI card too and was freaking for a bit. Luckily it was'nt one of the cards blacklisted. :D . Just hang in there and they'll work on the support for those cards more than likely.

---

### Post by SDL486 on 2009-04-24
Yeah so should I just wait until they work on support for those cards and where can I view this "blacklist"?  What are the best video cards for Ubuntu?  I hear nvidia is the best.

---

### Post by LT1Caprice57L on 2009-04-24
> **SDL486 said:**
> Yeah so should I just wait until they work on support for those cards and where can I view this "blacklist"?  What are the best video cards for Ubuntu?  I hear nvidia is the best.

I'd just go back to 8.10 until they improve the O/S drivers.

I did that and I'm fine with it.  I took the GDM theme and other misc appearance items from Janty and installed them on Intrepid, though.  Most notably the default 'human' GDM theme and the New Wave theme.  If you want to do that, let me know and I'll tell you how. (Though I just downloaded the 'New Wave' theme from [www.gnome-look.org](www.gnome-look.org), it's the exact same theme as found in Jaunty)

> **krazyd said:**
> Try this, and let us know how it goes:
[http://ubuntuforums.org/showthread.php?p=7027741#post7027741](http://ubuntuforums.org/showthread.php?p=7027741#post7027741)

I tried that and it made no difference for me.

Looks like I'll be buying a new laptop sooner than I'd previously thought... and it'll be something with an nVidia card.

---

### Post by SDL486 on 2009-04-24
Are nVidia cards usually the best for Ubuntu?

---

### Post by Prospero2006 on 2009-04-24
> **SDL486 said:**
> Are nVidia cards usually the best for Ubuntu?

Yes sir. I hate having to wrestle with ATI.
NVIDIA is king.

---

### Post by SDL486 on 2009-05-06
I solved my own problem by turning all effects off and using the config editor to get rid of the black outline that accompanies the windows when minimizing or maximizing.  I just want to thank everyone at these forums, you have all been very helpful.  By the way everything works really smooth now.

---

### Post by Mars73 on 2009-05-06
I have a laptop with Ati X1350 card and when updating to 9.04 I got a message that the card was not supported (something with proprietary) but went ahead and it installed the open source drivers.
I haven't seen anything that made me choose the Ati drivers (if it was available), these drivers work perfect and have full desktop effects on without a problem or speed issue. Don't know about the 9000 series though.

---

### Post by Citizin on 2009-05-06
Yes my 8600GT never lags and the compiz flow is smooth as silk. ATi has never had good drivers.

---

### Post by Don1500 on 2009-05-06
I have an ATI 9600 and aside from some splash inconsistancies I have no problem. I have the rotating box with 3-D windows, wobblie windows custome coloring and wall paper. I run HD DVDs as smooth as silk. But I am getting a new card soon, probably another ATI (HD something or other that won't go obsolete too soon).

---

### Post by Zyren on 2009-05-06
I recently got a new laptop with a radeon 3650 mobility 3d card, which is pretty powerful and should be able to handle ubuntu no problem. However, with the latest 9.4 catalyst drivers and compiz configured, it lags slightly. Everything is less responsive than with compiz off. Also, it takes a solid 2 seconds for a screen to maximize once its been minimized, which is a very annoying problem.

I have a 4 year only nvidia laptop with a geforce 6800 and i have had absolutely no issues with compiz and everything was smooth. Its kind of odd that such a new card can have issues like this, especially with such recently supported drivers

---

### Post by ssri on 2009-05-07
> **Zyren said:**
> I have a 4 year only nvidia laptop with a geforce 6800 and i have had absolutely no issues with compiz and everything was smooth. Its kind of odd that such a new card can have issues like this, especially with such recently supported drivers

Welcome to the wonderful world of crappy ATI drivers..

---

### Post by ayampanggang on 2009-05-08
SOME INFO:
I suppose it's not just with Jaunty, because just recently (about 3 months ago) I decided to switch to Debian + KDE 4.2 + compiz fusion and the same problem, i.e. the laggy when maximizing and opening a minimized window, appears to be there on Debian + KDE 4.2 too.

I then switched back to ubuntu from debian, thinking that the problem relies within the still unstable KDE 4.2, only to find the very same problem in ubuntu with gnome.

And what's strange is that the output of glxgears only yields about 1000FPS with my new laptop (ATI HD3400 series, core2 duo 2.26Ghz, 3MB ram) while my old one actually yields 1600FPS! (ATI Mobility X600, single core 1.6GHz, 2MB DDR1 ram). Well yeah it's true that glxgears is not meant to be benchmark measurement but surely these numbers meant something?

Mind you my old laptop was using older version of ubuntu (Hardy), and my new one is tested using the newset Debian and Jaunty.

So, I think the problem might rely on some newer implementation on the kernel, or maybe something else, which anyway shows clearly that there's some common problem outside of Jaunty, since the same problem appears in also Debian.

So now, no compiz fusion for me =(

Anybody has more info on this?

---

### Post by zeealpal on 2009-05-08
my old ATI 9550 worked without any drivers, cube and all. Now i got a 4850 and it works fine. I suggest you get the drivers from ati's website, not via ubuntu

---

### Post by edmicman on 2009-05-16
Nice to see I'm not the only one - I have a 600m, too, and noticed the same problem sincce the updrade.

How does performance go *backwards*?  I shouldn't have to downgrade to get better performance - I can't use whatever drivers or crap was being used in Intrepid??

---

