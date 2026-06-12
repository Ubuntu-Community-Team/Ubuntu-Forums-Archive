---
title: "[Intrepid] Compiz causes &gt;20s hang/delay after login"
date: 2008-11-08
forum: Desktop Environments
---

### Post by roots on 2008-11-08
hi there,

i upgraded to intrepid 2 days ago via fresh install, now on every login with compiz enabled i do get a >20s hang/delay before my desktop is ready. during that time, first only a black desktop-b/g is shown, loading-watch is ticking, then after 2..3s only my desktop wallpaper appears and the loading-watch is not ticking anymore. after another ~20s finally all other desktop elements appear and my desktop is responsive.

on hardy the whole login process took only approx. 3..5s (see my specs to explain this). i disabled compiz to check and found that metacity is available almost instantly after logon. in compiz i mainly use expo/viewport switcher without additional eye candy. but even if i reduce compiz settings to an absolute minimum the delay persists.

any help very much appreciated!


my sys/specs:

ubuntu hardy 8.10 (updates as of 11/07/08 )
compiz 1:0.7.8-0ubuntu4.1
nvidia 177.80 drivers

intel e8500
gforce 280gtx
4gb ddr2-800
2x ssd mtron 7535 raid0 @ areca 1210

---

### Post by paulluap_nl on 2008-11-08
I have the same problem. Im using 64bit version.

after login, I hear my hard disk spinning, after 2 seconds my wallpaper shows en everything stops, total silence and nothing happends for like 10 seconds (i can still move my mouse), and then I hear my harddisk again and gnome shows up and eveything is ready.

Very weird an very annoying.

EDIT:
I did some research, I did a login and switched back to a terminal running top. The only process running in the login delay is compiz taking about 20% cpu whole time. 

Also another weird bug: when i switched back to my graphical interface again, whole screen was white. But i could still click thinks, i had to login again to be able to use my desktop.

Is everyone using 64bit with this problem?

---

### Post by habtool on 2008-11-08
Same delay here

Not a deal breaker though, as my machine runs for days before I reboot

---

### Post by astoltz on 2008-11-08
It's a common problem.  I'm pretty sure there is a bug filed but I have not bothered to look it up.  Another thread suggested setting desktop effects to "none" and then adding the command "compiz --replace" to your startup programs (in System -> Preferences -> Sessions).  I've tried it and it does help - the desktop is available quickly like you'd expect (with metacity) but then there is a still short delay 'till compiz starts.

---

### Post by roots on 2008-11-08
> **astoltz said:**
> Another thread suggested setting desktop effects to "none" and then adding the command "compiz --replace" to your startup programs 

thanks a lot - this does in fact improve the situation a bit, yet it is by far not as quick as it used to be with hardy.

i had already searched bugtracker and did not find any corresponding entry, so i filed one myself. those who experience the same issue i would ask to kindly confirm the bug in launchpad, hoping it will speed up dev response:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/295454](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/295454)


thanks.

---

### Post by habtool on 2008-11-08
I can confirm that fix worked myside

---

### Post by Mega_Mike on 2008-11-25
> **paulluap_nl said:**
> I have the same problem. Im using 64bit version.

after login, I hear my hard disk spinning, after 2 seconds my wallpaper shows en everything stops, total silence and nothing happends for like 10 seconds (i can still move my mouse), and then I hear my harddisk again and gnome shows up and eveything is ready.

Very weird an very annoying.

EDIT:
I did some research, I did a login and switched back to a terminal running top. The only process running in the login delay is compiz taking about 20% cpu whole time. 

Also another weird bug: when i switched back to my graphical interface again, whole screen was white. But i could still click thinks, i had to login again to be able to use my desktop.

Is everyone using 64bit with this problem?

I experienced the exact same thing with 32bit Ubuntu 8.10 Intrepid when I attempted to switch to another viewport to look at the messages during login (nothing appears after pulseaudio warnings).  I am also using the 177.80 nvidia drivers with compiz.

---

### Post by Mega_Mike on 2008-11-25
Just want to add that setting desktop effects to 'none' and adding 'compiz --replace' to my session startup sped up the process greatly.  Thanks for the advice.

---

### Post by WattoDaToydarian on 2008-11-25
Yeah I am also having this same issue...
Lets get this fixed ppl!

---

### Post by baycoo01 on 2008-11-26
Charge stun. This 1-second stun has been one of the most annoying mechanics in a warrior's arsenal to date.we provide wow gold,cheap wow gold,warcraft gold. Charge is almost mandatory for entering combat effectively and forcing yourself to begin your stun DR (which resets after 20 seconds) with a 1 second stun just so you can get in melee range and generate a little bit of rage off of it seems very counter-productive, especially with a Protection-oriented build with 2 other controlled stuns (concussion blow and shockwave) and for any warrior in general as it shares DR with intercept stun. we provide wow gold,cheap wow gold,warcraft gold.Would it be possible to change Charge into a 1-second immobilize and 2-second interrupt? This would effectively yield the same results even for snare-immune targets (via hand of freedom) but would not annoyingly start your stun DR worthlessly. [wow gold](http://www.baycoo.com)[wow power leveling](http://www.baycoo.com/powerleveling-wow.asp)[wow power leveling 80](http://www.baycoo.com/powerlevelingreport.asp)[wow gold paypal](http://www.baycoo.com/wow_gold_paypal.html)[wow gold reviews](http://www.baycoo.com/wow_gold_paypal.html)

---

### Post by DevAdv on 2009-02-20
having the same problem.

will try the fix mentioned and see if it helps later.

-edit-

compiz --replace doesnt help one bit.

---

