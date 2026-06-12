---
title: "Switch users = black blank screen"
date: 2009-05-03
forum: General Help
---

### Post by scootre on 2009-05-03
I've installed Ubuntu 9.04 on a system that uses an Nvidia card.  Unlike last week when I tried Kubuntu and had nothing but graphics dramas, this install of Ubuntu using Gnome worked very well.  

For about three hours.

I have 4 user accounts.  Mine is the master account and the other three are Desktop accounts.  After setting up this thing the way I wanted, almost convinced 9.04 was OK, I used the button in the top right corner of my desktop to switch users to another account.

The screen when blank with only the cursor showing, which moves normally.

I waited a while.  No joy.  I tired Ctrl-Alt-F6, F7, F8.  Same.  I went to a console on F1, logged in and issued a shutdown -r.

After a reboot I get the normal login screen but ANY login I use - mine or the other three users results in the blank screen with the cursor.

The nvidia driver I'm using is v173.  My xorg.conf file has not changed for the past 24 hours.

The only setup changes I've made are changing the theme and colours for my desktop and also completely removing (via synaptic) Evolution.

A good search here and in Google reveals the same problem has been happening to people since Dapper.  But I am seeing wild suggestions with no fixes or threads that people have started that have had no responses at all.

Any suggestions as to how I recover from this? 

My wife uses this computer for her mail and web browsing and the WAF (wife acceptance factor) for 9.04 is plummeting rapidly.  :(  She now wants XP.  Ho ho.

---

### Post by scootre on 2009-05-03
Any of you "7044 users currently online".... got a suggestion?

---

### Post by scootre on 2009-05-03
How can I disable "Desktop Effects"... using the command line?

---

### Post by BslBryan on 2009-05-03
That's happened to me, as well.  I'm using hardy, but on the login screen after I suspend, I get a completely blank (white) screen.  

All I can suggest at the moment is just typing in your username and password blind and seeing if that works.  This is why I shy away from that, in most cases.  

If that doesn't work, Just right-click --> change desktop background --> visual effects --> none.

---

### Post by scootre on 2009-05-03
Hi BslBryan

Thank you for replying mate.

I've tried both entering my password and also entering username then password, blindly, but no luck.

Unfortunately, I can't right click anything... I have no desktop whatsoever - under any of the 4 accounts.  The only graphics I get is the normal login screen asking for a username then password.  But after entering login details for any of the four accounts the screen goes black.

I've tried booting into recovery mode and issuing this command:

$ metacity --replace

but get a response: unable to open X display"

At the recovery menu, I've also tried each of 

"xfix - try to auto repair graphics problems"
"grub - update grub bootloader"
dpkg - repair broken packages"

After these I would reboot and always end up with a black screen and the cursor.

I've had two weeks of this 9.04 mess.  I can reinstall 9.04 wasting yet more hours but I still don't know what caused this problem and how to fix it.

---

### Post by BslBryan on 2009-05-03
Disable desktop effects like this:

```
metacity --replace &
killall compiz compiz.real
```

---

### Post by scootre on 2009-05-03
No luck...

```
metacity --replace &
```
Unable to open X display

```
killall compiz compiz.real
```
compiz: no process killed
compiz.real: no process killed

---

### Post by BslBryan on 2009-05-03
try
```
startx
```

---

### Post by scootre on 2009-05-03
I've got a black screen with a workable mouse pointer so startx just tells me the server is already running for display0.

Looking at the log at /var/log/Xorg.0.log I see the last lines saying:

(WW) xf86CloseConsole: KDSETMODE failed: bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: bad file descriptor

---

### Post by BslBryan on 2009-05-03
```
sudo /etc/init.d/gdm stop
startx
```

Then, 
```
sudo /etc/init.d/gdm start
```

---

### Post by scootre on 2009-05-03
Nah no luck.

X seems to be starting and running but just not showing anything.

I've replaced my xorg.conf with the original (I backed it up after the fresh install).  Still same prob.

I appreciate your help.

---

### Post by delcypher on 2009-05-03
You try this command, it has worked for some people:
```
dpkg-reconfigure -phigh xserver-xorg
```

If that doesn't work you could try this below...

You could try editing you /etc/X11/xorg.conf file and using vesa driver instead.

[http://ubuntuforums.org/showpost.php?p=7184287&postcount=4]("http://ubuntuforums.org/showpost.php?p=7184287&postcount=4") I sort of explained how to do it at the bottom of the post in that link.

If that works then you can boot into a visual interface and then you can change the default window manager to metacity, as described [here]("http://ubuntuforums.org/showpost.php?p=7191960&postcount=2")

---

### Post by BslBryan on 2009-05-03
Maybe ```
vi /etc/X11/xorg.conf
```
to see if it detects your card?

Also, ```
cat /etc/X11/xorg.conf | grep Driver
```

and see if the drivers (the last two lines) are correct.

Maybe do a ```
sudo dpkg-reconfigure 
```

And, when my session file stops working, I've deleted
```
/home/username/.gnome2/session
```

And maybe
CTRL + ALT + F1
```
ps aux
```
look for the number of a process (#pid) called Bonnomo-activation
```
kill #pid
``` 

I'm sorry if none of this works for you, but if it doesn't I'm at a loss completely.  

Good luck, :)

---

### Post by scootre on 2009-05-03
Hi delcypher

I've already tried dpkg with no luck and various versions of my xorg - all which have worked on the system and survived multiple reboots today... until this problem.  X is running but not displaying anything.

I just cannot fathom how many stupid bloody problems have stayed with the releases through to now, v9.04.  Problems like this that I have found people complaining about for the past several years.

I would have thought my AMD2400 on a pretty standard mobo with nvidia 5200 gfx card would not be terribly obscure.  I spent last weekend battling with the same gfx problems others were complaining about: res locked in and staying at 640x480 or thereabouts.  Now today I have spent all my Sunday with this one.

I've not experienced a ridiculous problem like this before (been using Ubuntu since v6) - one that is so well documented in various forums that Google hits but at the same time one that nobody seems to have fixed in those threads dating back several years.  

I'm really disappointed with Ubuntu and, especially the 6 monthly release cycle that just regurgitates itself.

Are other distros, these days as unreliable as this?

---

### Post by BslBryan on 2009-05-03
If everything gets configured properly than Ubuntu is a very stable OS.  After hitting problem after problem, sometimes you have to use something else, though, or you'll have a constant headache.

One of the best things about Ubuntu is the community.  This forum has helped me out quite frequently, and I haven't found that in any other OS.  

One that comes close, I think, is Fedora.  Note that both Ubuntu and Fedora are funded by companies with lots of bees, if you know what I mean.  Have you considered trying that out?

---

### Post by scootre on 2009-05-03
@BslBryan
Firstly - thank you very much for continuing to try to help.

re your previous post:
xorg.conf - I've tried various incarnations of it both referring to nvidia (which had worked all day) and then nv and then the vanilla xorg.conf that is created at install time which still - normally - launches a desktop.

I tried:
```
ps aux bonnomo-activation
```
but there was no process found.

Even
```
pidof bonnomo-activation
```
returned nothing.

> **BslBryan said:**
> If everything gets configured properly than Ubuntu is a very stable OS.  After hitting problem after problem, sometimes you have to use something else, though, or you'll have a constant headache.

Yeah... I have to say, this is killing me.  The funny thing about all this is that Kubuntu 8.10 worked fine before all this on the very same hardware.

> **BslBryan said:**
> One that comes close, I think, is Fedora.  Note that both Ubuntu and Fedora are funded by companies with lots of bees, if you know what I mean.  Have you considered trying that out?

Yeah I have Fedora 10 right here.  I've decided I'll reisntall anyway because I can;t be sure what else will go wrong - given a lot of other complaints about 9.04 I have seen on the forums.  I could go back to Kubuntu or even Ubuntu 8.10 and know that it'll work fine.  Or I could try Fedora.  Either way... this release v9.04 has screwed me for two weekends in a row.  Arrrggh.  :)

---

### Post by BslBryan on 2009-05-03
Yeah, while the bleeding edge holds a bit of curiosity for me, as a student I can't afford to go with anything that's not extremely supported.  

So, It will be 10.4 LTS before I upgrade, probably.  I mean, Hardy proved hard enough for me to configure with my hardware, and with Fedora 10, my graphics card didn't load, and x failed to start, so I downgraded to Fedora 9, which didn't support my wireless chipset, etc. until I've finally got everything figured out, for the most part.  

In other words, I'm not bored, and I've got the LTS. :lol:

Anyway, I'm sorry I couldn't be of greater help.  I'll think about it more tonight, and try to see what else can be done.  Keep me posted on what you decide to do. :)

---

### Post by scootre on 2009-05-03
Hi BslBryan

I'm hearing you.  I gave it some thought and decided I'd go back to the safety and comfort of 8.10 and stay there, watching from the sidelines.  At least until the LTS comes out.

I'd downloaded the Live CD of Debian 5 but the burn of the ISO failed twice on my XP system with the error "illegal disk".  Huh??

So I mounted the ISO on my server running VMware and it loaded fine.  Looks OK but I really wanted to see how it'd go on my hardware and not some imaginary hardware set that comes from VMware.  I guess I'll just take my time, download the 5 disk set and swap out the HD in the Linux desktop puter and then try it  - all while leaving Ubuntu 8.10 in the swapped-out HD... I can't stand the thought of having to reinstall / fall back to 8.10 again... that'd be 3 times in 2 weeks.  :)

PS - and don't be sorry... you were excellent help mate.  And probably helped keep my faith in 'buntu.  :)

---

### Post by BslBryan on 2009-05-03
What program are you using to make the disc? 

Also, did you accidentally grab a CD-R instead of DVD-R?  Yeah, I know it's a stupid question, but I've done it before. :P

Anyway, good luck with Debian.  Here's to hoping you don't have to fall back again. :popcorn:

---

