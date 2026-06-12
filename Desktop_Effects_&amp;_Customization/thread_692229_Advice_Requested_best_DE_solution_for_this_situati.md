---
title: "Advice Requested: best DE solution for this situation"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by argraff on 2008-02-09
Hi all - looking for some advice here. I'm considering moving a non-profit I help with to Ubuntu. With their current system, it appears that the best solution is a super fast "server" with all important stuff and backups, and "drones" everywhere else. We're exploring the idea of the drone machines automagically VNCing into the server with a new session per. (We're pretending to have thin clients, without the complicated setup.)

So, basically, all ten computers could be logged in and using the server at the same moment.

While I'm not new to Ubuntu, I haven't explored Desktop environments, window managers, etc. Which ones should I be looking for (and links to instructions would be very helpful and appreciated)? I'm not concerned with eye-candy, just polish, stability and SPEED!

Many, many thanks in advance!

---

### Post by bwang on 2008-02-10
XFCE is the lightest desktop environment.
To install (assuming you're running normal Ubuntu):

sudo apt-get install xubuntu-desktop

IceWM:  lightweight window manager

To install:

sudo apt-get install icewm

Fluxbox: another lightweight window manager where you right-click for the "start menu"

To install:

sudo apt-get install fluxbox

---

### Post by argraff on 2008-02-11
Thanks for the instructions - another question, will that mess up Gnome? Do I uninstall Gnome? I'm trying to make this system as uncluttered as possible. And you switch all this in the sessions button on the login screen, right?

Do these update themselves as well? (I'm assuming they do, but I should ask, just in case.)

Sorry for all of the questions...

---

### Post by FuturePilot on 2008-02-11
If you do go with XFCE, instead of installing Ubuntu and then XFCE, you might be better off downloading the Xubuntu image. That way you won't have to worry about other unused packages and clutter. You can install multiple desktop environments side by side and they will not interfere with each other. You just select the one you want at the login screen. As long as they were installed from the repos, they will be kept up to date.

---

