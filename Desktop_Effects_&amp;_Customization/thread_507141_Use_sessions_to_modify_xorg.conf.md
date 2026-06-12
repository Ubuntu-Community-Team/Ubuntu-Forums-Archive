---
title: "Use sessions to modify xorg.conf?"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by neilneil2000 on 2007-07-22
Hi all,

As you will be able to tell from my lack of posting I am somewhat of a Linux noob.  But I am trying my hardest!

I currently have my machine set up with 2 identical monitors connected to a dual-headed X1800XT graphics card.

I have managed to install and configure beryl and xgl and have nice pretty effects but the desktop is cloned on the two screens which means effectively I just have the one.  I have looked into expanding the screen in this setup but it seems at 1152x864 there will be too many pixels for the drivers to handle.  This is OK and something I can live with when I am using 3D apps.

However when I am surfing the web I like to use the dual monitors so I reconfigured the system to use the ATI BigDesktop system and this works fine (with no 3D acceleration).

I have separate sessions when I log in for each (loading xgl or not), but each set up requires xorg.conf to be configured differently.

I can log in and change xorg.conf each time and then change session and this works fine but I would rather not have to do this.

What I would like to do is to choose a session, log in and have the system modify/replace the xorg.conf for me.

I have tried this by writing a bash script but the cp and mv commands always fail as the script is not being run as root. (Script is executed by the session launcher)

I am also wondering whether this would have any effect anyway since X is already started at the login screen, so would it need to be started again following the xorg.conf change?

Any help would be appreciated.

Many Thanks

Neil

---

### Post by kidders on 2007-07-24
Hi there, and welcome. :-)

Unfortunately, any time you alter xorg.conf, you have to restart X.

In theory, two (sort of similar) ways of addressing your problem come to mind, off the top of my head:
[LIST=1]
[*]Running two X servers simultaneously, and switching between them as you desire.
[*]Running only one X server at a time, restarting as required, but using a different xorg.conf each time.[/LIST]The trouble is that, by default, Ubuntu doesn't make it easy for you to have this sort of thing happen automatically, so your first step is to experiment a little & decide how you'd like your box to work. Then, we can worry about how to make it happen automagically for you. One possibility, for instance, might be to create a second [?]dm-like service. If you type **X -help**, you will notice the "-config" switch, which allows you to force Xorg to use a custom xorg.conf file. You *could* decide to create an /etc/X11/xorg.weird.conf, and have your second Xorg service use it.

What do you think?

---

