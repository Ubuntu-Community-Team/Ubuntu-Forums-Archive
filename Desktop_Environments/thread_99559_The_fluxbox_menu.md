---
title: "The fluxbox menu"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Therrol on 2005-12-05
Ok, so I installed ubuntu, and it looks awesome ;)

I downloaded my WM of choice, fluxbox, and installed it. After I log out and log back in into fluxbox, I notice two things.

The first, not very urgent problem, is that before loading fluxbox the computer just sits there. I've got a cursor, and I can move it around but I can't click on anything and there is nothing at all except a brownish background. This goes on for about 2 minutes.

The thing that I would really like help with, is that I have no fluxbox menu. Well, I sorta do. It just says "fluxbox default menu" as the title and all that it has in it is Xterm, restart and exit. I have the package menu installed, I reinstall it with no new effect. My ~/.fluxbox/menu file is empty too.

Any help on these issues?

---

### Post by duminas on 2005-12-05
1)
You can't use the version in the repositories without some problems.
Install the deb I'm going to link and it should work for you, though I did kill KDE support, so if you need those programs, you will need to rebuild fluxbox with --disable-xmb. If you like, I'll show you how to do that. You should know that Fluxbox, unless you have xmb disabled on Ubuntu, tends to love eating your CPU for breakfast (just check the output from **glxgears -printfps** if you want to see this).

[Fluxbox 0.9.14 deb](http://www.inflammare.com/fluxbox-0.9.14_0.9.14-1_i386.deb). Install it with **dpkg -i FILENAME** if you don't know how that works. You'll need to use /usr/local/bin/fluxbox to start Fluxbox in your .xinitrc. There's also a bit of code you need to use to make Gnome applications look decent under Fluxbox. That being the following in the ~/.xinitrc file (the gnome-control-center package needs to be installed):
```
# Make gnome apps play nice with Fluxbox.
GSDPID=`pidof gnome-settings-daemon`
if [ "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi
# And now start flux.
exec startfluxbox
```

Hopefully this helps. If I need elaborate, ask.

2)
Check in .fluxbox/init to see what it's pulling for a menu file. Also, fluxbox-generate_menu can help build a basic menu for you.

---

### Post by stevetone on 2005-12-06
I used the fluxbox in the Ubuntu repositories with only one problem. The long startup delay was eliminated by adding:

export LC_ALL=C 

to my .bash_profile

I used fluxbox_generate_menu as a starting point for my customized menu as well.

---

