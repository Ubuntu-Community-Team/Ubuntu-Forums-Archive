---
title: "going back to windows?  HELP!!!"
date: 2009-02-19
forum: General Help
---

### Post by LeadHop on 2009-02-19
something's gone terribly terribly wrong.

My intrepid ibex has gone wonky.  it no longer connects to the internet, keeps booting with a bunch of text on the screen (no matter how much i tweak the start up settings), lags incredibly in general, can't update, won't show the newest update on grub (shows -9, but not -11), and no matter how much i deal with it, constantly starts up with compiz even though i set it so that it shouldn't when i start the laptop.

i'm not sure what's happened, but it's a nightmare to deal with.  I'm on XP right now and compared to the problems i've had with ibex lately i feel like this is awesome.

I've been using ubuntu for well over a year now and loved it... then ibex came along.  i'm still willing to give it a go at going about the problem somehow:

a) someone walks me through this via aim (assuming I can get on the internet again).
b) do a clean reinstall of ibex
   i) ask for help in how to keep all my settings (saved tabs on swiftweasel, etc) in the new reinstall.
c) do a clean reinstall of hardy.
   i) see i above.
d) return to windows (I just got goosebumps writing that).

I'm really getting desperate for help.  the forums have been quite spotty in finding the help i need lately.  It's just that bad.

---

### Post by user-max on 2009-02-19
well, you probably have verbose mode on when you are booting your laptop, which explains console output.. I believe you enabled it when played around with bootup settings. I am running ubuntu 8.10 on my laptop ever since it came out without any problems. Are you using wifi or wired internet?

---

### Post by LeadHop on 2009-02-19
I am using both.  currently wire...  this thing's been really bad on me lately.  only to find that everything's fine in the world of windows.  it used to be the other way around. :(

---

### Post by handy on 2009-02-19
You may be better off using Hardy as it is more stable & will be supported until the next LTS (long term support) version is released in a bit over a years time.

---

### Post by user-max on 2009-02-19
Lets try to work through your problems one by one. What prevents you from using ubuntu first of all?

---

### Post by BrillianceLin on 2009-02-19
> **handy said:**
> You may be better off using Hardy as it is more stable & will be supported until the next LTS (long term support) version is released in a bit over a years time.

Yeah, I agree with you. 804 works better for me. I have tried several distributor in 2 days. 
Unbuntu 810 live-no internet connection under live mode =out
Fdeora 10 live-no internet connection under live mode =out
openSuses 11.? live- can not boot into live mode = out
Ubuntu 804 live-internet connection under live mode = stay & install
Still has some glitch on connection quality...

---

### Post by LeadHop on 2009-02-19
thanks for all the replies!

things i want to take care of:
1) grub issues.  It doesn't show the latest update - if memory serves, it should display 8.11, but it only shows 8.09.

2) splash screen.  the ubuntu symbol and loading bar pops up, then goes into "reading files needed to boot," etc.  it's quite bothersome.

3) compiz.  It used to be that if i had compiz on when i shut down it would be on when i reboot and it would be off if i shut it down with compiz off.  now it's on as default; I think i tried just about everything.

Look forward to the solutions!

---

### Post by LeadHop on 2009-02-20
bump.

---

### Post by pirate_tux on 2009-02-20
> **LeadHop said:**
> something's gone terribly terribly wrong.

My intrepid ibex has gone wonky.  it no longer connects to the internet, keeps booting with a bunch of text on the screen (no matter how much i tweak the start up settings), lags incredibly in general, can't update, won't show the newest update on grub (shows -9, but not -11), and no matter how much i deal with it, constantly starts up with compiz even though i set it so that it shouldn't when i start the laptop.

i'm not sure what's happened, but it's a nightmare to deal with.  I'm on XP right now and compared to the problems i've had with ibex lately i feel like this is awesome.

I've been using ubuntu for well over a year now and loved it... then ibex came along.  i'm still willing to give it a go at going about the problem somehow:

a) someone walks me through this via aim (assuming I can get on the internet again).
b) do a clean reinstall of ibex
   i) ask for help in how to keep all my settings (saved tabs on swiftweasel, etc) in the new reinstall.
c) do a clean reinstall of hardy.
   i) see i above.
d) return to windows (I just got goosebumps writing that).

I'm really getting desperate for help.  the forums have been quite spotty in finding the help i need lately.  It's just that bad.

Ubuntu isn't the only GNU/Linux disto you know...

There are more than other 300 distros out there...

---

### Post by jerome1232 on 2009-02-20
> **LeadHop said:**
> thanks for all the replies!

things i want to take care of:
1) grub issues.  It doesn't show the latest update - if memory serves, it should display 8.11, but it only shows 8.09.

2) splash screen.  the ubuntu symbol and loading bar pops up, then goes into "reading files needed to boot," etc.  it's quite bothersome.

3) compiz.  It used to be that if i had compiz on when i shut down it would be on when i reboot and it would be off if i shut it down with compiz off.  now it's on as default; I think i tried just about everything.

Look forward to the solutions!

Let's start with grub issues.

Can you show us your menu.lst, also would like to see what linux kernels you have installed. these two commands will show that.

```
cat /etc/boot/menu.lst
dpkg --get-selections | grep linux-image
```

---

### Post by user-max on 2009-02-21
2) Splash Screen:

Assuming you have start up manager installed (System > Administration > StartUp-Manager). If so, then open it up, and the first tab which is Boot Options make sure that: 'Show boot splash' is checked, and 'Show text during boot' is unchecked. That should get you rid of bothersome text on your screen. However, personally I don't have splash screen on my laptop, just text :,)

---

### Post by LeadHop on 2009-02-21
Here's what i get:

```

linux-image-2.6.27-11-generic			install
linux-image-2.6.27-7-generic			install
linux-image-2.6.27-9-generic			install
linux-image-generic				install

```

as far as the splash screen goes, i've already have those boxes checked/unchecked accordingly; it still comes up...  :(

---

### Post by user-max on 2009-02-21
what about your resolution? can you post whats in your usplash.conf file?

its in /etc/usplash.conf

---

### Post by WatchingThePain on 2009-02-21
If you leave me now, you'll take away the biggest part of me...oooooohhhh
ooh no baby please don't go.

---

### Post by LeadHop on 2009-02-21
from the usplash file:

# Usplash configuration file
xres=1024
yres=768

---

### Post by user-max on 2009-02-21
> **LeadHop said:**
> from the usplash file:

# Usplash configuration file
xres=1024
yres=768

try these..

xres=800
yres=600

Hope that helps.. I believe these are more standard.. Let us know how it went.

---

### Post by LeadHop on 2009-02-21
i was hoping setting the usplash would do it, but no dice.  :(

tried 800x600 as well as 1280x800 - no changes there.  It's just more frustrating because it shows the logo and the loading bar for a few seconds before going off into the text.

---

### Post by LeadHop on 2009-02-23
bump.

---

### Post by LeadHop on 2009-02-23
bump :-( man, no love on the forums these days.

---

### Post by LeadHop on 2009-02-25
bump.  I'm getting a bruise on my head from bumping so much.

---

### Post by user-max on 2009-03-03
Maybe we have to get some more experienced users in here to help you out.. However, you said Hardy worked better for you, maybe a fresh install of it would keep your system like you want it.

---

