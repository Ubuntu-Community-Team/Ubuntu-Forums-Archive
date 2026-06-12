---
title: "Confused about what version of Gnome I'm running"
date: 2012-05-30
forum: Desktop Environments
---

### Post by XEtedBear on 2012-05-30
I recently completed a clean installl of 11.10. After installing the latest proprietary driver for my hardware (Geforce FX5200) the system ran well, with Unity (which I don't like). I installed Gnome-shell using Ubuntu Software Centre. Now, at login, I can choose between Gnome, Gnome Classic, Gnome Classic (no effects), Unity or Unity 2D.

Choosing Gnome works but with excruciatingly slow performance.
Choosing Gnome Classic works fine (except that its Gnome Classic, which I take to mean Gnome 2-like)

I guessed that I needed to update Gnome to solve the performance problem and to enjoy Gnome 3, but the information from my system on what level of Gnome is installed completely confuses me:

System Monitor tells me I am running something called Gnome 3.2.1

Ubuntu Software Centre tells me that I have installed Gnome-Shell version 3.2.2.1-0ubuntu0.1

Ubuntu Software Centre also identifies 'Gnome' as "Gnome Desktop Environment, with extra components", at version gnome 1:3.0+1ubuntu1 and tells me that I haven't got it installed.

I have no idea how this desktop environment differs from the desktop environment I have got installed (if any - how do I tell?) or how it differs from Gnome-Shell. And I have no idea what upgrades, if any, there are which might address the slow performance I have with 'Gnome' - but not with Unity.

Any advice?

---

### Post by kansasnoob on 2012-05-30
The packages 'gnome' and 'gnome-desktop-environment' are actually the Debian versions of Gnome which were at the time Oneiric released at version 3.0.

The version of Gnome used by 'ubuntu-desktop' was at 3.2. Of course the Ubuntu default DE is now Unity but if you prefer Gnome Shell just install 'gnome-shell'.

If you prefer a classic DE you might find this helpful:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

---

### Post by haresear on 2012-05-30
I can't help on the Gnome version thing, but I'm pretty sure that with your FX5200 card, Unity is running in 2D even if you select Unity (3D) at the login. The terminal command 'echo $DESKTOP_SESSION' will tell you whether you are running Unity 2D or 3D.

Gnome, Gnome Classic, and Gnome Classic (no effects) all run on Gnome 3. 'Gnome' on the login menu is actually Gnome Shell.

---

### Post by XEtedBear on 2012-05-30
I'm having a little dififculty understanding why you submited this post as I cannot see how it relates to my original post:

- I already have gnome-shell installed, as stated, so there is no question of '...if I prefer gnome shell to Unity'
- I'm trying to get to the 'new' Gnome 3 look, as opposed to the Classic look and feel, as stated.
- along the way I am quite confused (for instance by the different code levels identified by Ubuntu Software Centre) and, as a user, cannot distinguish between 'shell' and 'desktop environment'. The introduction of terms like 'gnome-fallback', 'ubuntu desktop' and other terms increases my confusion.

---

### Post by haresear on 2012-05-30
My guess would be that your GUI performance issues have more to do with the window manager that is used with the various login choices. I found kansasnoob's post #3 in this thread to be enlightening:
[http://ubuntuforums.org/showthread.php?t=1984091]("http://ubuntuforums.org/showthread.php?t=1984091")

---

### Post by haresear on 2012-05-30
> **XEtedBear said:**
> I'm having a little dififculty understanding why you submited this post as I cannot see how it relates to my original post:

- I already have gnome-shell installed, as stated, so there is no question of '...if I prefer gnome shell to Unity'
- I'm trying to get to the 'new' Gnome 3 look, as opposed to the Classic look and feel, as stated.
- along the way I am quite confused (for instance by the different code levels identified by Ubuntu Software Centre) and, as a user, cannot distinguish between 'shell' and 'desktop environment'. The introduction of terms like 'gnome-fallback', 'ubuntu desktop' and other terms increases my confusion.

I was trying (badly) to say that 'Gnome 3' underlies all the Gnome login choices. The 'new' look is 'Gnome Shell' (called 'Gnome' on the login menu). 'Gnome-fallback' is the same as 'Gnome classic (no effects)' on the login menu. 'Ubuntu desktop' is just a 'meta-package' name -- a group name for a bunch of individual packages that are installed as part of the Ubuntu DE. I agree it can be pretty confusing.

Bottom line -- using my FX5200 card (with any driver) I've found that I cannot run Unity 3D or Gnome Shell adequately. The only 'new' look desktop my card can run adequately is Unity 2D (although I find it a bit laggy).

Post #9 in this thread is another attempt to clarify the Gnome terminology:
[http://ubuntuforums.org/showthread.php?t=1985601]("http://ubuntuforums.org/showthread.php?t=1985601")

---

### Post by Frogs Hair on 2012-05-30
The Gnome Shell version in 11.10 is 3.2 and 3.4 for 12.04. When you login.

Gnome= The Gnome Shell
Gnome Classic(looks more Like Gnome 2)
Gnome Classic No Effects (same as above) 

Screen Shots:[http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)


[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/)

---

### Post by haresear on 2012-05-30
The best experience I've found so far running Gnome Shell on my FX5200 video card was Fedora 15 -- it is somewhat laggy, but doesn't crash or do other weird things. I haven't tried later versions of Fedora. I also haven't tried the nVidia drivers with Fedora -- that might improve the responsiveness.

---

### Post by XEtedBear on 2012-06-01
> **haresear said:**
> The best experience I've found so far running Gnome Shell on my FX5200 video card was Fedora 15 -- it is somewhat laggy, but doesn't crash or do other weird things. I haven't tried later versions of Fedora. I also haven't tried the nVidia drivers with Fedora -- that might improve the responsiveness.

Many thanks for your advice here. Sorry to appear to be a bit tetchy in a previous post - that was a case of your post making it onto the forum, unknown to me,  before I finished creating my response to the input from kansasnoob.

The bottom line I conclude is that the best I can do, while retaining the FX5200, is to run with Gnome Shell 3.2 (as installed by default). It's not great, but it's easy for an old fogey with limited brain power like me, who grew up with OS/2 1.1, to handle. The performance is adequate with my entry level dual core AMD socket 939 processor.

Sorry, I tried Fedora about 7 years ago and was told, by a very red-neck (and proud of it) coal miner, from a hilly part of the old colonies, that I was too dumb even to qualify as pig-****, so would I please get off their forum? I was happy to comply.

---

