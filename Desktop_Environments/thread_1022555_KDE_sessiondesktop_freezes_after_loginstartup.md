---
title: "KDE session/desktop freezes after login/startup"
date: 2008-12-26
forum: Desktop Environments
---

### Post by crazups on 2008-12-26
Ok, this is my first time ever posting in any forum of any sort because I usually can figure out my problems by simply searching other forums, but I'm stumped.  My problem is with my KDE Session.  As soon as I log in I get my cool looking desktop, mouse pointer with a bouncy icon under it (looks like a gear i think it's the settings icon) then my other icons begin to load up in my panel.  Within 5 seconds the icon under my mouse pointer stops bouncing and I can't left click or right click , my icons stop loading i only get one or two on my panel.  I can however see my desktop and all else that belongs, I can move my mouse, I canl control alt F1 - 12 and get a terminal and switch to a dos looking screen and login but I can't do anything on the KDE desktop or session.  If you couldn't tell I'm a newbie.  Some recent changes Ive made was to install fglrx drivers for my ATI Radeon HD2400 trying to keep my Compiz working.  Which I was able to do!  But then I got greedy trying to configure my screensaver.  I couldn't remember how to access the settings for that (of course i've figured it out now) so I changed my display manager from kdm to gdm and restarted and now when I log into a KDE session it freezes, but a gnome session doesn't freeze.  Also possible worth noting i went and installed kubuntu thinkin it would fix the problem since i installed KDE using sudo apt-get install kde.  I'm about to "dpkg-reconfigure xserver-xorg" to reconfigure xorg.  I did a back-up at some point today but can't remember why but it's not in the X11 directory like I thought it would be.  Please help because I've already messed up my other two computers trying find a solution and one of them is the ol' lady's computer!!  Hurry, she's off work in 12hrs!!#-o

---

### Post by crazups on 2008-12-26
Alright!!....still batting 1.000 in resolving my own issuses!!  It turns out that "sudo dpkg-reconfigure xserver-xorg" solved the problem.  Things look some what different than the way I left them but it's atleast working.  Lost my Compiz effects, but I'll try it again tomorrow.  I hope this helps anyone having the same issuse.  Time to create a xorg.conf_backup while I can!!....HAHA!!

---

