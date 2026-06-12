---
title: "plasma desktop suddenly went permanently(?) blank"
date: 2010-02-06
forum: Desktop Environments
---

### Post by =JeffH on 2010-02-06
I'm posting this mostly as an FYI wrt KDE 4.3.2 Plasma desktop (vs. Gnome 2.28.0) -- both of which are presently "stock" in Karmic 9.10. The below tale/rant is related in KDE bugs 225765 and 225766. If, however, someone actually really fer sure totally knows how to fix my KDE plasma problem, then I might try it (I've already wasted too much time trying to fix it based on various posts herein). Otherwise, I'm just sticking with Gnome because I have my real day job work to do.

=JeffH
------
I am sorry that I don't have many helpful details for this report -- it is to mostly let you all know that yet another user had (apparently non-recoverable) difficulties with 4.3.2 plasma desktop. I happily used KDE (in concert with some gnome apps) on (k)ubuntu 6.10 for the last 3 years and just in the last week+ migrated to a fresh (k)ubuntu 9.10 x86_64 install. After the difficulty(ies) described below, I've fallen back to using Gnome + select KDE apps for the foreseeable future.

initial problems: IMHO, Plasma is overkill and I don't need or want most of its functionality. To me it is mostly unnecessary eye-candy. I was very happy with KDE 3.5.x (IIRC) and was able to tailor it to behave the way I require, and it didn't appear to hog an unjustifiable share of system resources. The main reason that I elected to use the KDE desktop over Gnome was tailorability. It features greater control over appearance and behavior options, and I was able to largely configure the panel + applets to behave in the style I prefer (just fyi, I don't use multiple desktops and run several apps with 10's of instantiated windows simultaneously, and so panel-based task management is critical to me).

I have a test/utility system on an old P3-based laptop on which I'm presently running kubuntu 8.10, so have had some plasma experience with that, and was pleased that plasma in kde 4.3.2 appears to have addressed several of the difficulties I have with it's earlier version(s).

The Actual Problem: So, I had gotten (k)ubuntu 9.10 installed and logged in and was busily tailoring my desktop for a couple hours and was putting the finishing touches on it -- setting the preferences of some applet (I don't recall which one) -- when suddenly the desktop went blank except that the default root desktop window wallpaper appeared (I'd changed the desktop to simply be my preferred solid color (brick red)), and I couldn't get anything to work except cntl-alt-delete brought up the logout dialogue. So I logged out, and back in, in the hopes that the difficulty would go away, but was greeted with the same blank desktop. AFAIK nothing "crashed" but I'm unable to know for sure (and I'm not a kde developer-type).

So I got online on another system and poked around for resolutions (most answers I found were in ubuntuforums.org) and tried the various "delete .kde/foo/foo file(s) and logout and login" and nothing worked. by this time I'd blown > 4 hours. I don't have time for this. I use this system for my actual day job, and since I support myself and eschew the corporate systems, it doesn't look good for me to take forever dorking around with my nerdish non-corp-standard setup.

So at this point I'm using Gnome (2.28.0) desktop plus select KDE apps (Konsole, amarok, kmix, kate) intermixed with some Gnome apps (e.g. nautilus) (and the typical mozilla ones). It's working for me. Gnome has certainly made improvements since whatever version it was on ubuntu 6.10. I can largely configure it as I need and it doesn't have all this unnecessary eye-candy (it offers and very simple dialog one can use to turn most all of it off).

Bottom lines here to relate to y'all here from a not-inexperienced user (who's done his share of software development over the years) is that I'm not going to use KDE + PLasma unless it offers a bullet-proof and simple switch to "turn off" all the extraneous (IMHO) eye-candy (a la Gnome), and deliver me a simple tailorable environment similar to the KDE 3.5 one.

I will of course continue to use select KDE apps, as long as they don't go off the eye-candy deep-end (the latest Amarok, unfortunately, is close).

Anyway, I just thought y'all should know.

thanks,

=JeffH

---

### Post by bobcollard on 2010-02-07
I have to agree with you about the eye candy and the instability.  I've used Kubuntu for awhile and I was experimenting with Gnome when I discovered Xubuntu with the Xfce desktop.  You might want to give it a try, you can work with the Live CD, but to get  to the guts of it you will have to install it.  What I have done is gotten my task bar to completely disappear unless I want it to show, then I installed Cairo Dock and made it also disappear.  This amounts to a very nice Application Launcher (Cairo Dock)  and a means to find what's running and bring it onto the desktop anytime you want it (The Panel).  I put a file of backgrounds (wallpaper) in it and it changes every time I reboot or close down and restart.  Nothing fancy, but, not boring either.  Altogether it takes less RAM and less HD to run and it's FAST!  That's less than either KDE or Gnome in size and faster than both.

---

### Post by =JeffH on 2010-02-09
So installing Xfce in parallel with Gnome & KDE works fine?  I'm presuming "yes", just curious if there's any big gotchas. If not, then I'll likely give it a spin.

thanks for the suggestion,

=JeffH

---

### Post by harrisonk on 2010-02-09
[SIZE=4]There shouldn't be any.

Harrisonk
[/SIZE]

---

### Post by bobcollard on 2010-02-09
> **=JeffH said:**
> So installing Xfce in parallel with Gnome & KDE works fine?  I'm presuming "yes", just curious if there's any big gotchas. If not, then I'll likely give it a spin.

thanks for the suggestion,

=JeffH
Other than a slight bloat on your HD no problems.  Synaptics and Apt take care of the dependencies.

---

