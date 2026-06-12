---
title: "Kamic and gnome, stability in Beta?"
date: 2009-10-07
forum: Desktop Environments
---

### Post by theZoid on 2009-10-07
I've always in the past jumped over to the next Ubuntu release at the time the BETA hit the shelves, and never had an 'real' problems other than a bug or two that didn't stop me in my tracks.

I'm hearing that Karmic is one of the buggiest Betas in recent history, yet I see a lot people using it since Alpha.  Is this true?  I have everything backed and considering making the change, but would like some input on Karmic if you please.

thanks !!

---

### Post by Incendia on 2009-10-07
> **theZoid said:**
> I've always in the past jumped over to the next Ubuntu release at the time the BETA hit the shelves, and never had an 'real' problems other than a bug or two that didn't stop me in my tracks.

I'm hearing that Karmic is one of the buggiest Betas in recent history, yet I see a lot people using it since Alpha.  Is this true?  I have everything backed and considering making the change, but would like some input on Karmic if you please.

thanks !!

I tried to use it but it wouldn't go past the new fancy boot screen.

---

### Post by ankspo71 on 2009-10-07
Hi,
Karmic Gnome is working okay for me, except I found a couple of apps that close unexpectedly. Pulse Audio (the service) closed on me but sound still worked. The 'User and Groups' in system menu takes 2 times to open. The new GDM requires clicking on my username first before I can see the sessions menu. All of the options in the 'Login Screen' options are gone... I'm still looking for where Ubuntu put them LOL. Overall it is stable and productive for me, but it has a few tiny bugs. Oh yeah, the start time for me is twice as log as jaunty... but this is beta. Also gdebi is broken too.

One important thing... if anyone installs Karmic Beta, watch out for those updates... there is missing packages/dependencies. I tried a partial update and Karmic never started after that. Now I don't have any updates installed.
James.

---

### Post by snotplop on 2009-10-07
I've been using it for over a week now and I'm actually very impressed.

Only a few things I've seen broken on all the hardware I've pushed it to:


[LIST]
[*][Fixed] Touchpad support on Acer Aspire One D250
[*]the gnome stickies applet is broken (all the stickies are intact)
[*]Likewise-open active directory support seems broken
[*]no screensaver/screenlocking (easiy fixed with $ sudo apt-get install xscreensaver )
[/LIST]
There's all sorts of nifty new little goodies all over the system though - particularly on laptops

---

### Post by snotplop on 2009-10-07
> **ankspo71 said:**
> Hi,
Karmic Gnome is working okay for me, except I found a couple of apps that close unexpectedly. Pulse Audio (the service) closed on me but sound still worked. The 'User and Groups' in system menu takes 2 times to open. The new GDM requires clicking on my username first before I can see the sessions menu. All of the options in the 'Login Screen' options are gone... I'm still looking for where Ubuntu put them LOL. Overall it is stable and productive for me, but it has a few tiny bugs. Oh yeah, the start time for me is twice as log as jaunty... but this is beta. Also gdebi is broken too.

One important thing... if anyone installs Karmic Beta, watch out for those updates... there is missing packages/dependencies. I tried a partial update and Karmic never started after that. Now I don't have any updates installed.
James.


I second the GDM headaches. Currently it doesn't seem there's an easy way to change any login options besides auto-login

---

### Post by shadowlands on 2009-10-07
the pars to unpack items are not working.  The program ignors the pars and tries to open items with gidget.

---

### Post by jjcv on 2009-10-08
> **snotplop said:**
> I second the GDM headaches. Currently it doesn't seem there's an easy way to change any login options besides auto-login

In GDM, click on your name and then have a look what appears on the bottom GDM bar.  :)

---

### Post by slakkie on 2009-10-08
> **ankspo71 said:**
> Hi,
One important thing... if anyone installs Karmic Beta, watch out for those updates... there is missing packages/dependencies. I tried a partial update and Karmic never started after that. Now I don't have any updates installed.
James.

You should NEVER install a partial upgrade. Unless you are 200% sure that it will not break your system. Wait a few hours for the archives to settle and then try the upgrade again.

The Karmic forums are filled with problems due to partial upgrades, people don't read the sticky and blindy accept anything.

See also [http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021) 
> 
Once you've started testing, do not upgrade your installation blindly - especially, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, always check the list of packages to be removed, upgraded and installed before each upgrade. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at packages.ubuntu.com) to see why a package may be being removed.

---

### Post by snotplop on 2009-10-08
> **jjcv said:**
> In GDM, click on your name and then have a look what appears on the bottom GDM bar.  :)


Oh I meant options to disable the face browser entirely

---

### Post by ankspo71 on 2009-10-08
Hi Slakkie,
Thanks for the link and tip. I remember reading it, but it must have slipped my mind. As of now the update manager still says partial upgrade, so I will continue to wait.
James

---

