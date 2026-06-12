---
title: "changing window manager completely"
date: 2015-06-10
forum: Desktop Environments
---

### Post by _fool on 2015-06-10
Hi folks,

New xubuntu 14.04 install here, instead of updating from my outdated 13.X.  I don't want to upgrade again soon so I am sticking with LTS.

I am trying to completely change to using the window manager ratpoison, preferably executed via ~/.xinitrc or ~/.xsession .  I managed to make this work through some combination of editing /etc/X11 files and other nonmaintainable surely-incorrect brute force type work in 13.X, but was thinking maybe I'd try to do it "the right way" this time.  All of the posts I could find when I googled were for changing just the WM but leaving XFCE running, which is definitely not what I want to do - I want to replace XFCE as well as its WM.

The helpful "user defined session" dropdown from my 13.X install is no longer there via the login manager, so I'm not sure where to start.  Further, the xubuntu 14.04 docs are pretty silent on operations like these.  I suppose that by default I might just try disabling X and I'd be happy to login via the command line and startx, but I'm guessing there's a way to get the login manager to Do The Right Thing and I'm just missing it.

Any suggestions?  Thanks in advance for your help!

---

### Post by Copper Bezel on 2015-06-10
When you're not using a full desktop environment, creating your own .xinitrc is indeed the preferred method - see [here]("https://wiki.ubuntu.com/CustomXSession"). If you follow all the steps, your custom session will be selectable from the Lightdm login screen alongside xfce. 

Some graphical apps *will *check the environment to see what session is running, and this can be a problem, specifically, with file handler associations. When I ran a Compiz standalone session configured with some xfce and Gnome parts, I had to set my script to export the session name as gnome, else, for instance, locations would load in the web browser instead of the file manager, because the handler failed. Depending on the kind of apps you're making use of (and if you're using Ratpoison, I'm guessing that this will be less of a problem for you) you might need to look into this as well. (The sample script in the page I linked does include this step as well.)

---

### Post by v3.xx on 2015-06-10
I find that arch is a big help

[https://wiki.archlinux.org/index.php/Xinitrc](https://wiki.archlinux.org/index.php/Xinitrc)

[https://wiki.archlinux.org/index.php/Start_X_at_login](https://wiki.archlinux.org/index.php/Start_X_at_login)

[https://wiki.archlinux.org/index.php/Ratpoison](https://wiki.archlinux.org/index.php/Ratpoison)

---

### Post by _fool on 2015-06-11
Thanks for that article;  it absolutely told me how to do what I wanted!  The only part I was missing was this section:

[https://wiki.ubuntu.com/CustomXSession#LightDM_configuration](https://wiki.ubuntu.com/CustomXSession#LightDM_configuration)

...and noticing that there is a tiny drop-down menu on the top of the login screen that I can use to change session type (in my previous version, it was on the login widget, so I hadn't thought to look in the upper right, faraway from the login box)

---

### Post by v3.xx on 2015-06-11
Congratulations :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

