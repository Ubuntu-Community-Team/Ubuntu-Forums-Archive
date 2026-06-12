---
title: "slow gnome session startup"
date: 2008-04-13
forum: Desktop Environments
---

### Post by jettero on 2008-04-13
I know I'm hardly the first person to have this problem.  I read as many of the posts I could stomach, but they all seem to be some different problem -- some people have bad hosts files, some people have a problem with the power-manager, etc.

My hosts file seems fine, and I can ping 127.0.0.1, localhost, myhostname, etc, so I sincerely doubt that's the problem.  I ruled out the gnome-volume-manager, gnome-power-manager, nm-applet, and various other things by disabling them in my session and then (to make sure) also moving the /usr/bin/filename to /usr/bin/filename.oops (temporarily) so they can't load behind my back.

I've spent about 5 hours on this (at about 5 minutes per try), but despite disabling each item in my session one at a time in two different ways, I have not been able to track it down.

My window manager loads successfully (loaded by gnome-wm), along with the gnome-toolbar and the evolution calander app.  The notification area remains empty for about two minutes until the gnome-power-applet and nm-applet icons appear at nearly the same time.

Again, I have disabled both of those completely, so it's whatever loads before them ... I guess.

My machine started doing this yesterday evening, when I deleted my ~/.gnome2/ directory by accident.  To rebuild and start from scratch, I removed ~/.gconf* ~/.config ~/.gnome* and rebooted.  

(I've done that step several times since then, to kinda completely start over and track down what's slowing my session startup so horribly.)

I wouldn't worry about the 90 second startup at all, except that nm-applet loads my wireless settings and ... well, computers are totally useless without a network connection these days!

I've pretty much given up on trying to figure it out myself.  I'd rather not wait 90 seconds for the nm-applet to load, but it appears to be beyond my skill level.

What can I do to track down whatever's slowing down my otherwise successful gnome-session startup?

[ubuntu 7.10 all up to date versions of gnome, etc]

---

### Post by ajgreeny on 2008-04-13
Just out of interest try making a new user and then log out and in again as that new user to see if it is anything to do with other settings or is system wide.  Interesting, though, as usually renaming or deleting the .gconf folder in home sorts out these types of problems.  The other thing to consider is any updates or additional programs you have (or have not) installed which could be causing this.  No doubt you've already thought about all of that, but it could be that you "can't see the wood for the trees", ie you are too close to the problem.

---

### Post by RTrev on 2008-04-13
Take a peek in /etc/usplash.conf

See if the resolutions there match what you are really using, and if they don't change them so they do.

HTH,
Bob

---

### Post by wolfc on 2008-07-11
I had the exact same problem on Fedora 9.

It turned out to be a window manager configuration problem. I had changed the window manager to compiz, but it didn't add '--sm-client-id' (default1 for Fedora 9 / default0 for Ubuntu).

In Ubuntu detection of the right window manager is pretty good, so either remove all your overrides or set WINDOW_MANAGER in .gnomerc. Do not add it to your session startup programs, that's the wrong approach.

---

