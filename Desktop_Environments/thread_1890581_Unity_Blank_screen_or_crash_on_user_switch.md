---
title: "Unity: Blank screen or crash on user switch"
date: 2011-12-03
forum: Desktop Environments
---

### Post by flying_surprise on 2011-12-03
Hi,

I am experiencing blank screen, session crashes or system freezes on user switching.

Example:

User A is logged in.
User B is also logged in.
User A's session is up.
User B switches to his session (using the menu in top right corner).
User B get's a blank screen with mouse cursor.
or
User B's session crashes (gets thrown back to gdm)
or
The whole system freezes completely.

This is pretty easy to reproduce. Just switch user some times and it will eventually occur. Anyone else seeing this?
This is Ubuntu 11.10 64-bit with all updates applied as of today.
I downloaded the Catalyst 11.11 driver, generated the packages and installed them. Problem stills exists.

Laptop is an Asus K70AF with 4GB ram and Ati Radeon HD5150.

---

### Post by flying_surprise on 2011-12-09
Nobody who has something to say about this?

---

### Post by bvanaerde on 2011-12-21
I'm having the same problem here.
Ubuntu 11.10 64bit with latest updates
Radeon HD 6870

It seems to occur less when the Catalyst drivers are not installed.
Also, when pressing CTRL+ALT+F7, I get the login screen again. So I'm not getting a system freeze.

---

### Post by bvanaerde on 2012-02-28
With the latest ADM drivers from their website, I'm getting system freezes as well...

---

### Post by mwk88 on 2012-03-10
I get the same problem; upgraded to 11.10 a few days ago, running 3.0.0-16-generic-pae kernel.

This is a pretty severe problem; happens almost half the time. I'm wondering why I'm not hearing more about it -- either not a lot of people regularly switch user (?) or something about our configuration.

A bit off topic, but I'm not very impressed with 11.10. Unity seems like a step backwards in both quality and user experience, and the switch to Banshee as the default music player was a non-starter for me, it cannot even index my 8000 songs. Also my upgrade failed because it did not install headers for the pae kernel so the graphics driver failed to install. What the heck is happening to Ubuntu quality?

---

### Post by ajesh on 2012-03-10
Same problem here...looks like Ubuntu 64-bit with ATI proprietary drivers seems to have this problem. Any help would be appreciated.

---

### Post by bvanaerde on 2012-03-13
I solved it by doing the following:
[LIST]
[*]if already installed, uninstall ATI drivers
[*]enable proposed repository
[*]install fglrx-updates
[*]disable proposed repository
[*]aticonfig --initial -f (not sure if this is needed)
[*]reboot
[/LIST]

---

### Post by mwk88 on 2012-03-20
I have NVidia GeForce 7600 GS, so ATI drivers aren't my problem.

I could believe it is a graphics driver bug though; I also have graphics refresh bugs on unlock screen. It's a different problem than the the switch user crash (happens after Unity is running again and I can fix by minimize/maximize the active window) but clearly there are some  driver bugs.

This thread may be related [http://ubuntuforums.org/showthread.php?t=1865506](http://ubuntuforums.org/showthread.php?t=1865506) the description "blank screen with just a flashing cursor top left" is what I get.

I have not found any smoking gun looking at logs, other than occasional networking errors that don't seem related.

There are some new things the native driver manager, NVidia Version 173-updates; what the heck is that? Is 173-updates newer than current? Anyway I'll poke around

---

### Post by mwk88 on 2012-03-20
Ah, well in my case (GForce 7600) I found another thread that may be related:

[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

a very long thread, the relevant quote:

"Nvidia Geforce 7xxx based videocard, this series is currently blacklisted in Ubuntu due to problems this GPU has with unity. It will not work in hardware accelerated mode. It can be forced in hardware accelerated mode but this usually causes the unity interface to freeze on startup.
Be patient, the problem seems to be solved with current beta driver versions. Or revert to old 173 version, witch will work, but is sluggish in comparison with unity 2d and current driver and might lack some features of the newer drivers"

So I've now switched to NVidia "V173-updates" driver but it'll be a few days before I can really tell if it's fixed.
--
Update: The older V173 (regardless of with or without "updates") does not solve the problem. The older v173 driver still has the same switch user bug, but also has more refresh bugs so a step backwards. Which makes sense I guess

I'm starting to think the 7600 with 256MB may just be too old so it is not getting much love from the Unity or NVidia folks, don't know who is at fault for these bugs but I'm more suspicious it is Unity as my 7600 was always A-OK before the Unity upgrade. Maybe Unity just expects a lot of VRAM available?

New test: I bit the bullet and just ordered a GeForce 520 upgrade. It's still a silent video card and reasonably low power (both reasons I liked my 7600), cost about $50 so we'll see if it behaves better with Unity...

---

### Post by mwk88 on 2012-03-30
Well, I have my spiffy-but-not-desired new GeForce 520 graphics card installed. Unity switch user no longer seems to just plain crash, but it goes to a black screen other with a small snow crash cursor sprite. If I wait long enough (eg 30 seconds) it seems to finish switch user but it fails to refresh the screen; then if I make some educated guesses on where to click I can gradually expose a workable UI. Needless to say this is not so successful with my other family members who share this system.

I did some more research, my conclusion: Unity in 11.10 is broken with more than one user logged into X at once. That is a pretty neat trick given how mature X multi-user support is.

Canonical, what the heck are you doing releasing a UI that cannot even do switch user successfully? It's like going back to the horrible Windows user login-driven process model.

I've given up. I have switched back to Gnome classic which was straightforward and it solved the problem. Excellent instructions available from:

[http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/)

[http://www.virtualhelp.me/linux/470-install-gnome-in-ubuntu-1110-oneiric-ocelot](http://www.virtualhelp.me/linux/470-install-gnome-in-ubuntu-1110-oneiric-ocelot)

---

### Post by bvanaerde on 2012-04-02
I noticed that CTRL+ALT+F7 will bring you back to the user login screen.
That is, only when the system hasn't crashed, ofcourse :)

---

### Post by dr_saaron on 2012-04-08
I've had what seems like a similar problem ever since upgrading to 11.10.  If I have 2 users logged in, the switch user doesn't work too well, but from the blank screen I can hit ALT-F7 or ALT-F8 to get to a login for the 1st and 2nd user to login respectively.  But I can't figure out how to get a 3rd user logged in since I can never get back to the greeter.  I never had anything like this on earlier releases.  So far we've gotten by just having family members share 2 accounts, but I really want to have each person use their own.

---

### Post by ac7ss on 2012-06-20
I have been trying to fix this as well. (not to mention that my screen lock has disappeared :(  ) The black screen does return to normal, after a couple of minutes.

I am going to try FGLRX-Updates and see if that helps.

---

### Post by Dr. Allcome on 2013-02-22
Hello everybody

Does have anyone news on this topic? Have anyone been able to solve this issue?

I tried with kdm/KDE and gdm/Gnome with the latest AMD Catalyst Driver 12.1 on a Radeon HD 6950 and 7970 but without success.

When switching user the one or other user is loosing its session.
It is really a big pity that this, a main function of the system is not working.

Please, if there is any input like a raised bug or rfe or any solutions or resolution attempts then please let me know here in this tread.

Thank you in advanced.

Kind regards,

Dr.Allcome

---

### Post by oldos2er on 2013-02-22
Unity has changed quite a bit since Dec. 2011, so it would be best to start a new thread and mention which version of Ubuntu and Unity you're using.

---

