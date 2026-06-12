---
title: "Switching between Gnome and KDE."
date: 2007-10-30
forum: Desktop Environments
---

### Post by Gaztech on 2007-10-30
Hello,

Try as I might I can’t seem to find a useful thread on this, so apologies if this has been asked before, it undoubtedly has but my search skills disappoint me.
 
	At present I’m running Gutsy 7.10 Kubuntu with Compiz-fusion installed and enabled. However being a nosy so and so I’d like to see what the Gnome desktop is like to use, so I was wondering how difficult it is to effectively switch desktops. Can the two be installed along side each other? Also if I decided to defect to Gnome is it possible to remove the KDE desktop environment and have just Gnome running? 

And finally, is having compiz-fusion installed likely to break anything during the switch, and as it is installed in KDE will it also be enabled in Gnome if the two run along side each other or will it need to be installed and re-configured to run on Gnome as well?

Thanks in advance for any help!

Gaz

---

### Post by bingoUV on 2007-10-30
You need not worry at all, Gnome and KDE are very friendly to each other. If you have installed kubuntu, just install ubuntu-desktop (could be a big download) from synaptic and you will have most of the Gnome goodies. Below, I will list some examples of their peaceful coexistence :

1. Run each other's apps. This is the way I do. I have a gnome session running. I use amarok (an excellent music manager/player) which is a KDE application. For file management, I use thunar (XFCE application) instead of nautilus.

2. One after the other. Logout from KDE, choose session. Select Gnome for the next desktop session. You log into Gnome.

3. Run a vnc server which runs Gnome. Connect to this vnc server inside your KDE session on the same machine. Now whole Gnome desktop is just a window inside your KDE session. You can fullscreen it if you want to momentarily focus on the Gnome-ness. For doing this, just write gnome-session in your ~/.vnc/xstartup script, and run the vncserver.

The possibilities are endless. Desktop effects do not cause any harmful side effects that I know of. You might have to enable compiz to run in gnome too.

---

### Post by haldean on 2007-10-30
It's really easy to install the two along side each other. Just run
```
sudo apt-get install gnome
```
(or install the gnome package from synaptic / adept) and it will install all of the necessary gnome packages. 

Then, if you want to switch, all you do is log out, click the menu button (default is in the bottom left corner), select "Sessions", select Gnome, then log in as normal. To switch back to KDE, you do the same but select KDE instead of Gnome.

I don't think that compiz-fusion will effect it at all (but I could be wrong). I think it will work in Gnome as well, but you're going to have to enable it. You can do that by going to System -> Preferences -> Appearance -> Visual Effects and selecting Normal or Extra.

---

### Post by Gaztech on 2007-10-30
Heh so it seems my fear of this was completely un-founded and it appears nice and easy :) 

Thanks very much for the help!

---

### Post by Epic Plecostomus on 2007-12-25
Ahha.   Great.  

Now does this work in reverse?  I have Gnome but want to try KDE.  Is the procedure more or less the same in this case or have the Computer Gods decided to pull something?  :confused:

In other words, spell it out for the nOOb please.  :biggrin:

---

### Post by TidusBlade on 2007-12-25
Yes, you can KDE on GNOME. Just look [here](http://www.psychocats.net/ubuntu/kde).
Or type this in the terminal:
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

