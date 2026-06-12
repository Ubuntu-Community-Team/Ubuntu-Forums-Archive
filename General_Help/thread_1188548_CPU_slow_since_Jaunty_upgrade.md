---
title: "CPU slow since Jaunty upgrade?"
date: 2009-06-15
forum: General Help
---

### Post by daegan_xavier on 2009-06-15
Hi,

I am a big ubuntu/linux newbie, so please be gentle.

Since I upgraded to Jaunty I've been noticing that the computer is very slow to respond, on almost anything.

I did a bit of digging around with system monitor and noticed that kded4 was eating a lot of CPU (around 50%) - I looked online and couldn't seem to find any clear explanation of what to do.

I have killed it for now, but I'd like to know
a) is there a better solution
and
b) how can I be sure that this was the problem?

When I run 'top', here are the results:
8976 idilia    20   0  613m 288m  39m R 41.8 29.1 453:03.57 firefox            
23161 root      20   0  366m  69m  14m S 25.5  7.0   1018:49 Xorg               
24457 idilia    20   0  3576 1420  468 S 10.3  0.1 183:47.34 dbus-daemon        
24507 idilia    39  19 56280 2212  920 R  5.6  0.2  98:03.80 trackerd           
24524 idilia    20   0 27276 2456 1420 R  5.6  0.2 106:12.46 python             
24516 idilia    20   0 18544 1516 1072 R  5.0  0.1  71:08.62 tracker-applet     
24462 idilia    20   0  161m  22m  18m S  2.7  2.2 349:35.94 pulseaudio         
11772 idilia    20   0 38460  14m 9732 S  2.0  1.5   0:01.24 gnome-terminal     
24481 idilia    20   0 58300 8660 4844 S  0.7  0.9  16:09.35 metacity           
11966 idilia    20   0  2448 1184  912 R  0.3  0.1   0:00.05 top                
12716 idilia    20   0  127m 9080 6364 S  0.3  0.9   0:03.35 knotify4   

Do I have stuff running I don't need?

Many thanks for any help,
Daegan

---

### Post by ohzopants on 2009-06-16
First of all, top does not provide a full list of running programs.  To obtain such a list you should use "ps -A".  This list won't really help us help you though, since no one other than you knows what you "need" to have running on your system.

I'm not sure what you mean by you killed kded4.  From your top output it looks like you're running gnome (metacity is gnome's default window manager).  Did you log out and log back into a gnome session?

One thing that may improve your performance is to use gnome apps in gnome and kde apps in kde.  There is nothing wrong with running kde apps in gnome (or vice versa) but in order to do this your computer will need to load a bunch of libraries from the other window manager to run the app.  These extra libraries being loaded can slow you down.

---

### Post by daegan_xavier on 2009-06-16
> **ohzopants said:**
> First of all, top does not provide a full list of running programs.  To obtain such a list you should use "ps -A".  This list won't really help us help you though, since no one other than you knows what you "need" to have running on your system.

I'm not sure what you mean by you killed kded4.  From your top output it looks like you're running gnome (metacity is gnome's default window manager).  Did you log out and log back into a gnome session?

One thing that may improve your performance is to use gnome apps in gnome and kde apps in kde.  There is nothing wrong with running kde apps in gnome (or vice versa) but in order to do this your computer will need to load a bunch of libraries from the other window manager to run the app.  These extra libraries being loaded can slow you down.

For killing kded4, I looked up the processID and then I killed it.

I didn't know about gnome vs kde - if I'm running gnome, then I imagine, according to what you say, I should stay with gnome apps.  How can I know which ones are kde and which ones are gnome?

Many thanks.

---

### Post by ohzopants on 2009-06-19
The performance improvements that can be made by running solely native apps (as a rule of thumb gnome apps are usually name gSomething and KDE apps are usually named kSomething) are negligible on relatively modern hardware.

Also, what version of Ubuntu did you upgrade from?  I believe desktop effects are enabled by default in Jaunty, turning those off/down has always increased performance for me.

---

### Post by daegan_xavier on 2009-06-19
> **ohzopants said:**
> 
Also, what version of Ubuntu did you upgrade from?  I believe desktop effects are enabled by default in Jaunty, turning those off/down has always increased performance for me.

I was with Hardy Heron before - if desktops effects = visual effects, they're off.  I removed a bunch of kde programs that I had installed, things seem to be running a bit faster now, but it's still slower than it was with Hardy.

---

