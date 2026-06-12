---
title: "Weird Key-delay and repeat behavior"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Kadin2048 on 2005-12-30
I'm having a (to me, anyway) bizarre problem with my keyboard and keypress behavior using Kubuntu Breezy. Here's the scenario:

What happens is that every time I press a key, there is a significant delay, I'd say about half a second or so. Then the image appears onscreen. If I press a key for more than even a fraction of a second (more than a very quick peck) it will repeat WILDLY -- sometimes spitting out half a line of typed letters at once.

Today I moved my Ubuntu box from one location to another -- which to the computer means nothing except that the wireless network has a different SSID -- and all hell broke loose.

Problem 1) I can't get it to connect to the WL network anymore. In the process of trying to fix this, I opened up System Settings > Network Settings and tried to get it to give me a list of wifi networks (which I used to do). It refuses, and I've had no luck getting it to network. However this became the least of my problems. Apparently because of something I did, and I preface this by saying I modified *nothing* in the Keyboard or Accessibility control panels, the keyboard is all messed up. The system is rendered basically unusable.

I've gone into the System Settings and tried to reset all the keyboard-related settings to defaults, but nothing seems to matter. I've also tried different keyboards, and tried the Ubuntu box's keyboard on another computer -- it's not hardware. There are also not any problems with the mouse or clicking, and the delay isn't being caused by the computer being busy -- otherwise, responsiveness is good.

In this thread ([http://www.kde-forum.org/post/55769/lastpost.html#post55769](http://www.kde-forum.org/post/55769/lastpost.html#post55769)) someone said that maybe there is a config file in ~/.kde that needed to be deleted, but I couldn't find anything in there that seemed keyboard-specific.

Can anyone tell me what to do? Or what file to delete to just reset all the keyboard stuff to defaults?

I'm learning maybe to just not touch the GUI control center if this is what happens just by trying to change the wifi network. Ouch.

UPDATE: I tried logging into Gnome and the same thing happens, so it's not just a KDE issue ... I don't think?

---

### Post by John.Michael.Kane on 2005-12-30
you may have to edit the xorg config file

---

### Post by John.Michael.Kane on 2005-12-30
edit double post

---

### Post by Kadin2048 on 2005-12-31
Any thoughts on what I should edit/change/check in there?

I just looked through it and couldn't find anything obviously amiss. I'll run the debian reconfigure program and see if it fixes anything, but other than that I'm pretty lost when it comes to editing that file (for anything other than the basics, anyway ... monitor resolutions and such).

---

### Post by coaxx on 2006-07-11
I have the same problem here! Any suggestions?

---

### Post by Kadin2048 on 2006-07-11
I have no idea what exactly I did, but the problem went away a little while ago. I "shotgunned" a lot of stuff, so I can't tell you precisely what fixed the problem ... I reconfigured xorg's settings, did a lot of plugging/unplugging of my USB stuff, reset a lot of config files to their default values ... basically everything I could think of save reinstalling. Somewhere in there, the problem went away.

For what it's worth, I've since upgraded to Dapper, and I think that just as a cohesive OS, Kubuntu is *much* improved. A lot of rough edges and little annoyances are gone compared to Breezy; so if you're still running the old version, I suggest that you make your first step "dist-upgrade" and work from there. If you still have the problem then, probably time to start a new topic in the Dapper forums.

---

### Post by coaxx on 2006-07-11
thanks for Your advice. Upgrading to dapper is maybe not a good ideo because I have done some extra installations with automatix.

---

