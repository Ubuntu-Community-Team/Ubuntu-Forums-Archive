---
title: "Gnome2 in Ubuntu 11.10"
date: 2011-10-13
forum: Desktop Environments
---

### Post by Mahkoe on 2011-10-13
I didn't want it to come to this, but I've haven't found anything on google. You guys remember gnome2 in 10.10? I do. It was the best DE I've ever used. Before I realized what using linux meant, I was compelled to install it only because I saw gnome2 and decided that it was for me. Well, I upgraded to 11.04 a while back, and it had gnome2, but it was a little buggy. I waited 4 months for 11.10 hoping that the gnome2 interface would work just as well as it did in good 'ol 10.10. Well, imagine my surprise when it's not an option at the login screen, and I can't for the life of me find the ppa or the packages or anything. I can't bring myself to use Unity for some reason and I agree with Mr. Torvalds' views on gnome3 ([http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/](http://www.theregister.co.uk/2011/08/05/linus_slams_gnome_three/)). So, long story short, how do I get gnome2 on 11.10, or even better, because 11.10 and 11.04 were both faster, is it possible to downgrade? Thanks a lot

Also, if nothing should work, could I reinstall 10.10 on my ubuntu partition WITHOUT formatting, so that it just replaces the system files but doesn't touch my other ones?

---

### Post by IWantFroyo on 2011-10-13
Gnome 2 is dead and officially unsupported. If you install "gnome-shell" in 11.10, I think it gives you a fallback mode that resembles the old Gnome 2, though.

---

### Post by Mahkoe on 2011-10-13
Looks it it's re-install all your software on a fresh install of maverick time again

---

### Post by crdlb on 2011-10-13
You should at least take a look at gnome-session-fallback (GNOME Classic at the login screen). Just hold Alt to modify the panel, and install gnome-tweak-tool to change themes, fonts, etc.

---

### Post by 3Miro on 2011-10-13
Gnome 2 is dead.

Gnome-session-fallback (available in the Software Center) is pretty close, it may be good enough for you.

Some people are working on Mate, which is Gnome 2 resurrected, but it is unclear when or if it will become main-stream.

In general, if you like Gnome 2, you should take a look at xfce4. It is not Gnome 2, but it is more similar than not. Xfce usually takes a bit more time to setup just the way I want it, but in the end, I think it is better than Gnome 2.

---

### Post by merlinus on 2011-10-14
> **crdlb said:**
> You should at least take a look at gnome-session-fallback (GNOME Classic at the login screen). Just hold Alt to modify the panel, and install gnome-tweak-tool to change themes, fonts, etc.

Thanks a bunch for this info!  But I cannot seem to move the application launchers on the top toolbar.  They are locked in place.  Can this be done?

Previously I could right-click and have the option to uncheck the lock feature.

---

### Post by oldfred on 2011-10-14
I installed fall back and may be able to live with it. I am still on Maverick and tried Unity. My wife complains about changes so I did not attempt Natty, I could not get Natty's unity to work well but with its fallback,it seemed ok. but I knew that was soon to be obsolete as it was gnome2 and everything was going to be gnome3.

But this is pretty close and with some tweaking which seems to be available, I may use this.

sudo apt-get install gnome-session-fallback
sudo apt-get install gnome-tweak-tool

Return to Ubuntu Classic Desktop in Ubuntu 11.10
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)
How to Fix common Gnome 3 issues on ubuntu 11.04 (Natty)
[http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html](http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html)

[http://ubuntumanual.org/posts/405/gnome-3-and-shell-a-complete-user-guide-part-2](http://ubuntumanual.org/posts/405/gnome-3-and-shell-a-complete-user-guide-part-2)

---

### Post by critin on 2011-10-14
I'm pretty disappointed.   I've looked forward to upgrading but since my machine can't handle Unity, I have to use Classic.   I haven't kept up with the news, but no more gnome 2 means I can't upgrade Ubuntu anymore.  I don't know if I can use Gnome 3 because I don't know what kind of hardware it requires.  (I'm assuming it will need what Unity needs)  

With no support either, guess I better not mess with it too much.  Now I wonder if regular updates break something, (or I do) down the road -- I'd be stuck with a broken desktop.  Reminds me of XP with no more support.  Guess Ubuntu is targeting new, high-powered pc's now.    :(

---

### Post by crdlb on 2011-10-14
> **merlinus said:**
> Thanks a bunch for this info!  But I cannot seem to move the application launchers on the top toolbar.  They are locked in place.  Can this be done?

Previously I could right-click and have the option to uncheck the lock feature.

Applets are now anchored to left, center, or right. This makes the panel much more robust with resolution changes. Within those constraints, you should be able to move any applet by holding alt, right clicking, and selecting 'Move'

---

### Post by neoman4426 on 2011-10-21
> **critin said:**
> I'm pretty disappointed.   I've looked forward to upgrading but since my machine can't handle Unity, I have to use Classic.   I haven't kept up with the news, but no more gnome 2 means I can't upgrade Ubuntu anymore.  I don't know if I can use Gnome 3 because I don't know what kind of hardware it requires.  (I'm assuming it will need what Unity needs)  

With no support either, guess I better not mess with it too much.  Now I wonder if regular updates break something, (or I do) down the road -- I'd be stuck with a broken desktop.  Reminds me of XP with no more support.  Guess Ubuntu is targeting new, high-powered pc's now.    :(

There is still a fallback mode by default, just this time it is Unity-2d for people who can't run Unity-3d. much less system intensive, but pretty much the same other than having less configuration and less eyecandy. other than that, you could easily install any number of other DEs. openbox (my current main), LXDE, XFCE, etc.

---

### Post by astraluxkl on 2011-12-05
> **Mahkoe said:**
> I didn't want it to come to this, but I've haven't found anything on google. You guys remember gnome2 in 10.10? I do. It was the best DE I've ever used. 
.....


I know this .. after ubuntu 11.04 .. i am using ubuntu 10.10

in ubuntu 11.10 .. clasical desktoip is horible

---

### Post by astraluxkl on 2011-12-05
The best for me is Ubuntu 10.10 .. 11.04... also has gnome 2 but is is not working so fine as in 10.10

gnome 3 is horible .. it is not for working .. it is like a slideshow that i don't need

sorry ubuntu team but at the moment ubuntu 10.10 is great ..

:popcorn:   - ubuntu 10.10 forever


after ubuntu 11.10 i hope you will return as a option classical desktop from Gnome 2

---

### Post by oldtimer7777 on 2011-12-05
> **astraluxkl said:**
> The best for me is Ubuntu 10.10 .. 11.04... also has gnome 2 but is is not working so fine as in 10.10

gnome 3 is horible .. it is not for working .. it is like a slideshow that i don't need

sorry ubuntu team but at the moment ubuntu 10.10 is great ..

:popcorn:   - ubuntu 10.10 forever


after ubuntu 11.10 i hope you will return as a option classical desktop from Gnome 2

I was using 10.10.. But did a fresh install of 11.04 after using 11.10 since beta 2 recently.  I just have to say, I'm with the OP on this thread.  I would to see something like Mate become available.  Unity is great for tiny little 10 inch devices, but I need what Gnome 2 provided me when it comes to a desktop environment.   I could list the reasons many of us Gnome 2 fans share, but I will save myself the time explaining why, and just post some links so you can see what everyone else has to say about it:

[http://www.cc-c.de/german/linux/ubuntu.php](http://www.cc-c.de/german/linux/ubuntu.php)
 and this
 [http://www.zdnet.com/blog/perlow/why-ubuntu-1110-fills-me-with-rage/19103](http://www.zdnet.com/blog/perlow/why-ubuntu-1110-fills-me-with-rage/19103)

---

### Post by chejose on 2011-12-05
Well, I would agree about not liking the new Ubuntu look. But one solution is to install 10.04. It has the "classic" Gnome 2 desktop.

José

---

### Post by efflux on 2011-12-30
Ubuntu is a dead distro now. It's a disaster. It ended at 10.10.

I've been using Debian for ages. I upgraded recently with testing and got Gnome 3. I was concerned at first due to Ubuntu unity disaster. However, Gnome 3 on Debian is great.

I can't even recommend Ubuntu anymore to people I'm trying to move to Linux. Mint is the best for newbies.

---

### Post by cwklinuxguy on 2011-12-30
There's always the MATE project, which is forking Gnome 2 and attempting to continue it's development. They have a ppa in launchpad, but I'm unsure how complete it is. Might wanna do some research to find the newest version of their project :)

---

### Post by Elfy on 2011-12-30
Closed.

---

