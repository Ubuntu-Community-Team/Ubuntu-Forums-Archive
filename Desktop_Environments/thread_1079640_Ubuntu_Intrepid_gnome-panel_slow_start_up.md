---
title: "Ubuntu Intrepid gnome-panel slow start up"
date: 2009-02-24
forum: Desktop Environments
---

### Post by esteeven on 2009-02-24
Hello. Nice to meet you all. ):P

I am new to Gnome : I have been a Kubuntu user for years but KDE 4.2 is not to my liking (yet) and I have to say that I am really enjoying my first real taste of Gnome-Desktop.. I have it on this Ubuntu 8.10 desktop (fresh install - P4 2gb) and a Debian Lenny box (P4 512mb.) On this desktop, gnome-panel starts very very slowly. It takes about 50 seconds for it to appear. It is not slow once started.

The same thing happens using Metacity and Compiz. It also happens using a Gnome-Openbox session.

I have tried deleting all panels and rebuilding them. Same problem.

When I open a pure Openbox session and then start up gnome-panel manually, it appears almost instantly, behaving as I know it really should.

On my Debian Lenny box, I have no such problem. The panel appears quickly.

I have no idea where to look for a solution to this problem. I imagine that Gnome or Ubuntu are running something behind the scenes but I don't know what. Tracker is off.

Please help.
Many Thanks!

---

### Post by deepclutch on 2009-02-24
this means ,some applet is taking more time to load in Gnome Panel.you please trace which applet that you have added to it?

---

### Post by esteeven on 2009-02-24
Fair comment but the same thing happens if I remove my panel and create a fresh one and leave it completely empty. Just a grey bar ..... :confused:

When I log in, I get the same result.

---

### Post by deepclutch on 2009-02-24
It can be time applet or the Gnome Menu.I don't think you are running panels blank :p .look at both top and bottom panels carefully.did you see any extra thing added?for me ,I have sensors-applet(procy temp,graphics card temp display) ,but that doesn't slow down.
anyways ,open a terminal once in Gnome and run this :
```
killall gnome-panel
```Now ,Look How fast gnome-panels are reloading?Does it is STILL Slow to load?

Next ,I suspect some ~/.gconf entries.but I am no expert to comment on this.also ,with a via unichrome onboard card on one of my systems sometimes back ,I experienced such a problem.kind of confusing;I know.

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803)
EDIT:
sources suggests that due to mounting network shares(samba,ftp etc) ,gnome-panel can take time to load.
Look at /etc/hosts file.

---

### Post by esteeven on 2009-02-24
I will have a look at /etc/hosts .... thanks. Good idea.


I have just removed my single panel again (by creating a new one and then deleting mine) .... the new one is blank. Same issue. What I can't understand is why running

$ gnome-settings-daemon
$ gnome-panel

in Openbox gives me a fast-loading panel.
:-\"

---

### Post by esteeven on 2009-02-25
Still got the problem. It's the same with a new user on the same system. Obviously, it's something that Gnome does on start up .... the problem is still not there in Openbox. I have checked /etc/hosts and it seems pretty standard to me.

---

### Post by esteeven on 2009-02-27
Hmmmmmmm! I added gnome-settings-daemon & gnome-panel to the default /etc/xdg/Autostart.sh file for Openbox. Openbox-session opens quickly and I believe that this is Gnome (with Openbox.) Is there anything else I need to add that makes Gnome fully Gnome (if you see what I mean?) :)

---

