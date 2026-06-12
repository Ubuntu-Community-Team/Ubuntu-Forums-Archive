---
title: "How do I get a GNOME3 desktop?"
date: 2011-10-13
forum: Desktop Environments
---

### Post by Psyael on 2011-10-13
I installed gnome-session-fallback (GNOME Classic) to give it a whirl, and decided I wanted the regular GNOME3 desktop like defaults in Fedora. This package is gnome-shell, but after installing it and logging into it I'm still getting GNOME Classic interface with the launcher bar, Applications pulldown menu, etc.

I've tried to uninstall everything and try again. removing everything installed by both packages according to Software Centre, then tried gnome-shell again. Still classic.

I realize a lot of people prefer the classic GNOME launcher and desktop, but I'd like to give the new interface a try. Help!

---

### Post by Baneblade on 2011-10-13
[This should help]("http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html")

---

### Post by Psyael on 2011-10-13
Those instructions use a new repository. Aren't these packages included with the default repositories in Oneiric? [This blog post](http://www.techdrivein.com/2011/09/gnome-shell-in-ubuntu-1110-first.html) suggests as much.

---

### Post by kurt18947 on 2011-10-13
Installing the gnome-shell package was all I had to do. When you log on, click on the little star-like icon to the right of your user name.  Gnome is the first item listed on my machines and what you want. Ubuntu & Ubuntu 2D are the unity screens. I also downloaded the fallback package so have Ubuntu Classic and Ubuntu Classic - no effects which are the gnome 2 - like screens.

---

### Post by Psyael on 2011-10-13
Well, I'm well messed up, then; because GNOME and GNOME Classic produce the same vaguely 2.x desktop that most people only get in GNOME Classic mode.

I'll keep this thread open and try any ideas people give, but if I can't get it fixed by the weekend I guess I'll do a clean install.

---

### Post by crdlb on 2011-10-13
Open a terminal and run ```
gnome-shell --replace
``` Post the output in code tags.

---

### Post by 23dornot23d on 2011-10-13
This sounds like a graphics card problem ......

what graphics card do you have ?

If its Nvidia or ATI it may need the drivers setting up first ......

ok ( yep good call )

**gnome-shell --replace**

in a terminal will give the reason why its not working .........

---

### Post by Psyael on 2011-10-13
Okay, done that.

```
$ gnome-shell --replace
Window manager warning: Missing composite extension required for compositing

```

It's hung up on that, trying to close the window informs the task is still running and I'll have to kill it.

Critical parts of my interface (launcher, taskbar, etc) are gone now, and ctrl-alt-del doesn't work, so I'll have to do a hard reboot.

---

### Post by crdlb on 2011-10-14
> **Psyael said:**
> ```
$ gnome-shell --replace
Window manager warning: Missing composite extension required for compositing
```

Are you using Xinerama? Because that is incompatible with compositing. If not, attach your /var/log/Xorg.0.log.

---

### Post by Psyael on 2011-10-14
I do have the packages libxinerama1 and x11proto-xinerama-dev installed. I'm not sure when they got on there, as their description doesn't make them sound like anything I would use. I also see a xinerama reference in that log file you mentioned.

However, trying to remove either of them would remove scores of other packages that I use, ranging from Flash to Solitaire.

I'm using an NVidia, with post-release drivers. I've made GNOME3 work on Fedora when I goofed off with it on a spare drive once, so I doubt it's a hardware profile issue.

---

### Post by crdlb on 2011-10-14
It looks like Xinerama is enabled in /etc/X11/xorg.conf (or /etc/X11/xorg.conf.d/*.conf). If you want to use two monitors with compositing, you need to use TwinView.

---

### Post by Psyael on 2011-10-17
Hello, I was out on business this weekend, so I wasn't able to get back to this thread.

It does seem Xinerama is enabled, but I don't have two monitors nor any expectations to use two. How should I go about removing it? I tried removing the packages in Synaptic but it wanted to remove 96 some odd dependent programs along the way.

---

### Post by crdlb on 2011-10-17
Look for 'Option "Xinerama"' in /etc/X11/xorg.conf. If you didn't do it intentionally, you may have enabled it with nvidia-settings. You can probably just rename the xorg.conf and boot without one.

Xinerama isn't the only reason Composite could be disabled, but it's the most likely if 3d acceleration is otherwise working. If you don't see anything, post your /var/log/Xorg.0.log .

---

### Post by alexpotter on 2011-10-17
You don't need to replace anything.

Do in the terminal:
```
sudo apt-get install gnome-shell
```

And log out, and under the gear icon (11.10) next to your name, click GNOME and it should log you into GNOME 3

:)

---

