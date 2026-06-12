---
title: "unable to remove gnome-panel"
date: 2009-11-02
forum: Desktop Environments
---

### Post by Xelort on 2009-11-02
Hi there people.

I upgraded today to 9.10 from 9.04, and now can't apply my previous configuration.

I used Gnome with Compiz drawing the desktop (not nautilus), thunar as file manager, and fbpanel as panel.
In 9.04, to get that, i just removed nautilus and gnome-panel with Synaptic and the rest was easy. Now, i can't remove them without removing gnome-session too, "killall gnome-panel" keeps restarting it, and can't find the way to autorun fbpanel (as well as using thunar as default file manager).

Tried gconf-editor, changing /desktop/gnome/session/required_components/panel to the value "fbpanel" and /desktop/gnome/session/required_components/filemanager to "thunar". Tried also changing xinitrc, /etc/gdm/PostLogin/Default, gnome-session-properties to add a little script that kills and load stuff... none of that worked so far. Dunno what else to do :(

So, removing gnome-panel, replacing it with fbpanel, and using thunar instead of nautilus, all this in Ubuntu 9.10.
Any help?

Thanks in advance.

---

### Post by earthpigg on 2009-11-03
> I used Gnome with Compiz drawing the desktop (not nautilus), thunar as file manager, and fbpanel as panel.

i do not think you where using gnome at that point, sir.

recently, gnome has decided to make all their components more "integrated" and requiring each other. its annoying, but thus is life (it annoys me, too).

with the level of customization you are doing, have you considered a command-line install and adding exactly what you want (breaking your unneeded dependency on gnome in the process)?

this isn't tested, but i think in theory you could...

command line install.
install xorg.
install xdm or the display manager of your choice.
install openbox or the basic window manager of your choice.
install fbpanel.
install thunar.
install other things you are used to -- synaptic package manager, firefox, compiz, etc.

configure openbox (or the WM of your choice) to launch fbpanel and thunar when it starts.

i bet you will end up with a slimmer and faster system in the end.

if you wish to give it a shot, go ahead and do so. when/if you get stuck, let us know so we can help you out. many of us here to command line installs and build from there on every ubuntu install. 

one thing many have problems with is finding the package names for the little things that ubuntu comes with that make life easy. i have an incomplete list here: [http://sites.google.com/site/masonux/home/ease-of-use](http://sites.google.com/site/masonux/home/ease-of-use)

---

### Post by Hugolp on 2009-11-03
I am in the same situation. Previously gnome-panel was integrated in gnome as well, but with changing some configuration with gconf you could run gnome without gnome-panel. Anyone knows how to do this in Karmic?

**SOLVED**: Ok, so I found out how to do it. First, I tried this without AWN working, and it did not work, probably because it did not find a replacement for gnome-panel, so it launched it anyways. So, before doing this, you need to have AWN or the panel you are using configured to start on start-up.

Open a terminal, and execute 'gconf-editor'. You will see a tree style configuration screen. Expand desktop, inside desktop expand gnome, and inside gnome expand session. Select required_components (inside session) and on your right you will see three values to configure. One is called 'panel' and is set to 'gnome-panel'. Double click to edit it, and delete it, so its blank. Press enter and quit. Now log out and log in and gnome-panel should not be there (remember, only if you have another panel set).

---

### Post by fnogb on 2009-11-04
That particular method (from Hugolp) didn't work for me. 
I've tried it a couple of times with no luck.
I've also tried editing the default values in /var/lib/gconf/. Didn't help either.
I had to chown -R ~/gconf, as several directories and files were owned by root. I guess this is not default behaviour - it seems illogical to me, so I'm guessing it's something I've done myself a long time ago for some strange reason.

Does anyone have any other ideas I could try?

---

### Post by pythonsyntax on 2010-10-12
didn't work for me.And i useing ubuntu 10.10

---

### Post by xircon on 2010-10-12
```
sudo mv /usr/bin/gnome-panel /usr/bin/gnome-panel-old
```

Log out/in

---

### Post by bobcollard on 2010-10-12
Could just change to Xubuntu, get Thunar by default and use Compiz your way.  Sorry, I cannot sympathize, I don't like gnome.

---

### Post by cepr on 2011-03-26
> **Xelort said:**
> 
Tried gconf-editor, changing /desktop/gnome/session/required_components/panel to the value "fbpanel" and /desktop/gnome/session/required_components/filemanager to "thunar". Tried also changing xinitrc, /etc/gdm/PostLogin/Default, gnome-session-properties to add a little script that kills and load stuff... none of that worked so far. Dunno what else to do :(

So, removing gnome-panel, replacing it with fbpanel, and using thunar instead of nautilus, all this in Ubuntu 9.10.
Any help?


It works for me on Ubuntu 10.10, did you cleared any previous saved session ?
```
rm ~/.config/gnome-session/saved-session/*
killall gnome-session

```
If you saved a previous session with gnome-panel running, it will start again even if you modify gconf settings.

---

### Post by king.katlo on 2011-08-11
It may be risky to remove the panel as you have to configure some files, an alternative I may recommend is to:

**right click on the panel>properties>**

and then **check out **expand and then **auto-hide** the bar.

***By so you would rarely bump into it because its small especially if you removed all elements from the panel.***

Cheers,

God bless you.:)

---

