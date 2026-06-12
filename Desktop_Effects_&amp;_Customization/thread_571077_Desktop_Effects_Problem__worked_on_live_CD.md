---
title: "Desktop Effects Problem:  worked on live CD"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by the tempest on 2007-10-08
So I downloaded the 7.10 release of Ubuntu after perusing other releases in the past.  I ran the live CD on a Gateway 500MC that I received second hand.  The desktop effects worked fine on the live CD.  After installation to the hard drive when I try to enable desktop effects after installing the compizconfig-settings manager, I get the error "desktop effects could not be enabled."   This is even when I try to turn on typical effects.  Can someone point me in the right direction to getting this solved?

As far as I know the specs for the system are:
P4 2.4 GHz (no HT)
512 MB RAM
20GB HDD
ATI Radeon rv100 (radeon 7000)

I have tried changing the graphics adapter to the ati radeon driver with no success.  Any help would be greatly appreciated.

---

### Post by ryanVickers on 2007-10-08
They work off the live cd!?!  Wow!  How does it do that - are like *all* drivers in existence included and enabled by default!? :p

I would check other 3D apps to see if *they* work...

---

### Post by the tempest on 2007-10-08
yeah that's what I found odd.  It works for at least the Extra addons on the when running off the live CD but once I install and update and then install the compizconifg-settings-manager it no longer works.

I even just booted off the Live CD again just to make sure I wasn't seeing things but all the extra visual things work fine (desktop shift, wobbly windows, etc)

I will try and use the settings I find when booting fron the live CD.

---

### Post by gtrtx on 2007-10-09
> **ryanVickers said:**
> They work off the live cd!?!  Wow!  How does it do that - are like *all* drivers in existence included and enabled by default!? :p

I would check other 3D apps to see if *they* work...

Actually, I ran the Gutsy tribe 5 livecd a while back, and I actually had to enable the driver. So it wasn't there by default. If I remember correctly, It actually enabled it for me when It asked if I wanted to enable desktop effects. Now, my memory isn't all that great, but I remember the process being rather seamless and of course it may have changed since then.

---

### Post by FuturePilot on 2007-10-09
> **ryanVickers said:**
> They work off the live cd!?!  Wow!  How does it do that - are like *all* drivers in existence included and enabled by default!? :p

I would check other 3D apps to see if *they* work...

Yes you can enable them on the live CD now. Even if you have a Nvidia card. Just enable through the Restricted Manager and log out. X is restarted automatically and when you come back the the desktop everything is wobbly.

---

### Post by the tempest on 2007-10-09
Well I reinstalled off the Live CD and on a fresh install the Extra Visual Effects radial button is working and I have wobbly windows.  I just now downloaded and installed the compizconfig-settings-manager.  We'll see what happens when I change to custom.  And after that I'll try to update.

---

### Post by the tempest on 2007-10-09
ok it seems to work so far... 

although I am running with the custom1 monitor at only 1280X960

so thus far I have:
Installed off the Live CD
Installed compizconfig-settings-manager

---

### Post by the tempest on 2007-10-09
Okay.  I think I found the problem.  The visual effects stop and become unusable when I change the monitor from Custom1, what it was after the installation and on the live CD, and change it to my Sony monitor, which is a Multiscan 20seII.  Now I have changed it back to a Generic Monitor 1280X1024.  And the visual effects are back and working.  

Is there something wrong with the monitor driver?  

Also I am fine with using a generic monitor driver however when I am using the generic monitor driver I cant expand the number of desktops.  (i.e. when I open the app for the desktops preferences there is no roller to change the number of desktops only the roller for how many rows to display on the bottom bar).

Any ideas?


P.S.

I'm sure some of my language is pretty vague if not completely wrong.  I'm still learning what everything is called.  I am coming from over 20 years using windows and 10 years professionally as an engineer.

---

### Post by the tempest on 2007-10-09
Also I changed it from the custom1 monitor to the Sony monitor because the custom monitor wouldn't allow me to change the resolution from 1024X900 to a standard size of 1280X1024.

But now I cant change the number of desktops with the generic monitor and i cant get the desktop effects to work with the Sony monitor.  And I cant get the custom monitor back.


Any ideas would be helpful.

---

### Post by ryanVickers on 2007-10-09
I;m kind of lost - your sure you installed the graphics drivers and it all is correct?

---

### Post by the tempest on 2007-10-10
Ok.

I think I have resolved this issue.  

Under System > Administration > Screens and Graphics

I had selected my monitor.  Sony GDM-20se3t

When this monitor is selected compiz desktop effects would not work at all.  

However when I changed it to either Generic Monitor or Sony GDM-200PS it works just fine.  I dont know exactly why it wont work with the one Sony monitor and does with the other.  

Also I have realized that I was not looking in the right place to choose the number of desktops.  Sorry I'm still learning a little bit here.  So now I've got compiz running nicely.  Cube works great.  Minimize, close, open, wobbly effects, etc all work great.

It's finally shaping up to be a nice system.

I think I should add a little more ram.  Eventually this system is probably going to be turned into a DVR/emulator/torrent system.  But that's once I get the hang of everything.

---

### Post by ryanVickers on 2007-10-10
Good to here.  Just one question of mine now...
> System > Administration > Screens and GraphicsWhat exactly have they done?!  Last time I checked *that* didn't exist!... ;)

---

### Post by Forlong on 2007-10-10
> **ryanVickers said:**
> What exactly have they done?!  Last time I checked *that* didn't exist!... ;)
[http://www.ubuntu.com/testing/tribe5](http://www.ubuntu.com/testing/tribe5)

---

### Post by ryanVickers on 2007-10-10
ooo! :)

---

