---
title: "new to (k)ubuntu older to linux"
date: 2005-12-14
forum: Desktop Environments
---

### Post by ravenon on 2005-12-14
Okay, my first post: hello to all.
I am coming over to ubuntu from Mandriva (3 years). Decision was based on reviews and I had various problems with MD 2006.
Ubuntu was cool-no problems from the start on a Toshiba P30 laptop save the usual suspend/hibernate (no big deal to me, this is a desktop replacement type laptop).
I added Kubuntu and then the backports of KDE 3.5--nice. Here are some likely minor problems that I have not been able to overcome.
First, in the beginning, Firefox and Thunderbird opened quickly (4 sec); overtime they have gone up to about 12 secs. Anybody else experience this?
Secondly, the KDE networking will not allow me to enable the wireless card. Its behaviour is to enable the card and then almost instantly disable it. Moreover, the wireless no longer starts at boot as it had--somewhere I have screwed up a config file? I can enable the wireless with the ubuntu/Gnome network tool.
Third, for some reason, I no longer can start the Gnome desktop. It fires up with sound and all, gets to the point of putting up the gnome panels and then they simply flash in and out. Should I reinstall gnome-panels package?
These are no big things to me. I use KDE most of the time, like to switch to other desktops for a change once in awhile. Wireless is not a problem since I know how to start it after boot. Finally, I like firefox and thunderbird, but konqueror and kmail are really just as nice.

any help/suggestions would be appreciated

---

### Post by mlomker on 2005-12-14
> **ravenon]First, in the beginning, Firefox and Thunderbird opened quickly (4 sec) said:**
> 

They'll always be a little slower given that they're gnome apps.  My machine is fairly new so it's not much of a difference.  You could give [prelinking]("http://www.ubuntuforums.org/showthread.php?t=74197") a try.  I hear it's a big improvement for OpenOffice.

> Secondly, the KDE networking will not allow me to enable the wireless card. Its behaviour is to enable the card and then almost instantly disable it. 

I don't use the graphical applets, myself.  The key file in Debian is /etc/network/interfaces.  You'll find the most important networking config settings in there.

[quote]Third, for some reason, I no longer can start the Gnome desktop. It fires up with sound and all, gets to the point of putting up the gnome panels and then they simply flash in and out. Should I reinstall gnome-panels package?

I'm not too familiar with gnome but that sounds like a reasonable idea.  I'd recommend making a post on the gnome desktop board about that.

---

