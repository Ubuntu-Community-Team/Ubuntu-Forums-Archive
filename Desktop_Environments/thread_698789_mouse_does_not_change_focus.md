---
title: "mouse does not change focus"
date: 2008-02-16
forum: Desktop Environments
---

### Post by GameboyHippo on 2008-02-16
I've run into one of those problems that I'm the only one in the universe having this problem and thus I'll probably not get an answer, but here goes.

My desktop environment has been working great up until this morning.  My wife noticed that when she would hold down the left click button, it would only affect a certain window.  I tried testing this and the problem is throughout the system.  This is difficult to explain.

Basically while the mouse gladly moves anywhere I want it to, the x server will only respond to clicks in a random window.  Like right now, I can click and hover over stuff in my firefox window, but my desktop does not respond to clicks or hovers.  Heck only the workarea in firefox responds to clicks and hovers.  Not the menus above.  Not the back and forth keys or the URL bar.  Other programs will also not respond to mouse clicks and hovers.

It's like the mouse internally cannot change focus.  This doesn't just happen with firefox, that was just an example.  I tried reconfiguring my X server and that doesn't help.  I'm all out of ideas.  Like I said, I probably put up a SEP field and nobody else knows what I'm talking about or how to fix it.  If by some miracle, someone knows anything about this, please let me know what to do.

---

### Post by GameboyHippo on 2008-02-16
It looks like it magically fixed itself.  I tried everything.  I tried reinstalling xorg (since it affected both gnome and KDE, I assumed it was an xorg problem.)  I tried booting without my nfs home folders, I tried switching to KDM, I reconfigured X.  Nothing worked.  So I got mad, shut down my machine, went grocery shopping, came back and everything works.  Doesn't make sense since  rebooted several times trying to debug this.

Anyway, if anyone has a guess as to why this happened and what fixed it, let me know.

---

### Post by s3gfault on 2008-02-17
i have bad news for you.  What is the difference between a reboot and a coldboot?  nothing except for the internal temperature of the system.  If your mysterious, baffling, software independant problem is magically fixed after your system is allowed to cool off, then most likely you have overheating components.

I can't imagine what kind of hardware failure could be causing this exact behavior (damage to the bus between the ps/2 and processor? or USB bus damage?) but the clues right now are pointing to faulty components.

---

### Post by djuniah on 2008-03-30
I have the same EXACT issue.  When it occurs (its not an instant thing, it usually starts happening after i've run it for a while) and it usually only starts when the computer is in a period of heavy load (browsing the web while watching a video for instance).  I have yet to find any solution for it, but alt-tabbing and manually clicking on them on the bar at the bottom of the screen still work to change focus when the problem pops up.  That gets me by until i can restart X again to get it to stop for a while.  INCREDIBLY annoying though...

Out of curiosity, what are your specs? Specifically GPU related cause i'm betting this is a compiz-fusion/X related issue

I'm running:
ATI Radeon Mobility 200m
1.6Ghz Songle core AMD sempron
Ubuntu 7.10 with desktop effects enabled

---

### Post by dphurst on 2008-05-15
None of you are alone!  I have gutsy installed on several laptops and a desktop and all are working perfectly.  None are exactly alike in installed packages due to the fact I'm learning Kubuntu after using SuSE for years.  The latest desktop I just finished installing Gutsy on has no hardware problems I'm aware of, yet has this weird mouse focus effect.  I've installed the basic similar set of packages from the Kubuntu repos.  The application that seems to cause this KDE freeze up is called Maestro and is from [www.schrodinger.com](www.schrodinger.com).  This app when started doesn't work reliably after a couple of minutes if the KDE focus stealing prevention is set to none.  If set higher then the window manager seems to immediately freeze up.  I've noticed 100% usage of one of the cores, however, killing the Maestro process doesn't not recover the KDE window manager.  The mouse will still move on the screen but isn't able to cause any effect when clicking on any part of the desktop.  Recovery requires a kdm restart.  I don't get any messages in any log I've looked at so far.  Messing with focus stealing prevention and mouse focus seems to affect the length of the stability of the app but doesn't have a combination that fixes the problem.  I've never seen this before.  This is a Dell Precision workstation with a nvidia quadro FX3450 w/Core2Duo 2.1GHz.  Gutsy is fully patched.  I initially installed Kubuntu but now added the ubuntu-desktop meta package so I can try out gdm.  kdm with a gnome login still had the same problem.  So, the current thought is hardware?  I can run some tests using the Dell diagnostics.  Haven't had any problems with OpenSuSE 10.1 that was installed on there previously.  No hardware faults showing up in any logs.  The box runs 24/7 since we use the boxes for computations at all hours.

The app, Maestro, runs under OpenSuSE 9.3 to 10.3 and Centos 4 with any problems.  OpenSuSE 10.1 and 10.2 did have some quirks with needing focus stealing prevention in KDE set to low rather than normal.  Any thoughts would be appreciated!

I should add here that I'm using KDE 3.5.8 with just normal patch updates as of today.  The effect GameboyHippo explained where only clicking on the title bar switches focus is a real effect I've experienced.  Also, with different focus stealing prevention settings the only way to switch focus can change to the taskbar app's entry on the taskbar.  With maximum focus stealing prevention the Maestro app freezes KDE immediately after clicking on any button in the Maestro application.  With no focus stealing prevention, KDE and Maestro will run for a while and then KDE will freeze after enough maestro functions are accessed.  If I knew how to get KDE or Maestro to tell me the error then maybe I could make some progress.  Right now I can't find any errors under /var/log in the message, daemon, kernel, Xorg.0.log, syslog, dmesg and so on.  You get the idea!
Dow

---

### Post by djuniah on 2008-05-15
Problem was seemingly fixed in hardy.  Havent seen it since the upgrade

---

