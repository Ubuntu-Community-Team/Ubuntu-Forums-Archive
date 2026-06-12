---
title: "is thera an easy dual monitor config?"
date: 2009-08-12
forum: Desktop Environments
---

### Post by Goonie on 2009-08-12
Hi all

I'm one of those that has tried to go MS free many times but always failed. I usually try once a year to install linux and make it function at work. It's that time a year now :)

One of the things I can't get to work is extending my desktop onto a secondary monitor. I'm not really looking for a solution involving hacking the Xorg config file or anything that needs to be done each time I hook up a different secondary monitor. I have several offices and I have various types of monitors with different resolutions and connecting them needs to be hassle free. I have an Ati card and I installed catalyst manager which seems to have a feature much like windows does but of course it won't work. I've googled and searched the forums but haven't seen any solutions that are simple enough. Any magical solutions? Thx

Regards.
Gunnar
Iceland

---

### Post by AmerNewbieInDE on 2009-08-12
well, sounds like you are where i am... but i run nvidia, as long as your graphics card suppord two monitors, under system, prefs, display, you should easily be able to configure what you want.

---

### Post by Goonie on 2009-08-12
well I know my hardware supports extended desktops since I've been using it on windows without problems. Also I should add that cloning the desktop in Ubuntu is not a problem, just fails when I try to extend it. If I try what you suggested (system-prefs-display) the display configuring window hangs and I have to force it down. Catalyst manager detects both displays but I can't configure them side by side. I tried xrandr but it was just the same, didn't allow extending the desktop. The option was grayed out. 

Regards
Gunnar
Iceland

---

### Post by gjoellee on 2009-08-12
I have not watched the howto video here, but it might help. Link: [http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/](http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/)

---

### Post by Goonie on 2009-08-13
Hi

I watched the how-to but I think it was not really doing anything differently from what I had tried already. It said one should install EnvyNG as a step in configuring my display but from what I've seen that only installs the proprietary graphics drivers which I've already done. I will give it a try just the same later today to see if it works any better that way.

---

### Post by asmoore82 on 2009-08-13
Xorg has completed the transition to configfile-less operation!!

In fact, you will find that in Ubuntu 9.04, everyone's favorite fixit command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
actually re-instates a near empty xorg.conf file.

As long as you stick with open source video drivers,
You will find that the full range of Xorg configuration,
including dual monitors with extended desktop or cloned desktop,
is available to you on-the-fly through the `xrandr` command.

You can experiment with this command and once you get the exact
settings you want, you can paste that command into a launcher.

I'm not currently at my laptop, but when I am I can show you 3 launchers that I have made.

---

### Post by Goonie on 2009-08-13
Thank you all for the replies. This sounds promising, I'll try the open source drivers when I find the time later today. Will the open source drivers work with eye candy stuff like compiz?

Regards,
Gunnar
Iceland

---

### Post by Goonie on 2009-08-13
Oh my... things just took a turn to the worse. I disabled the non free ati drivers and I guess I should have rebooted before I installed the open source drivers because when I restarted the machine it won't boot anymore. Just shows scrambled colors on the screen. I can get to a root console prompt but I don't know what to do to fix this. running in recovery mode doesn't work. Can you tell me if I can fix this from console? thx.

Regards,
Gunnar
Iceland

---

### Post by Goonie on 2009-08-13
Ok I'm getting somewhere. I managed to get back in after uninstalling fglrx from console. Tried xrandr (the gui actually) but no luck with setting the dual display. the radiobuttons (cloned and extended) are greyed out. I then used the built in display manager and voilá I got an option to extend my deskop :) I had to relog which was a minor annoyance but it worked... almost hehe. Now my menus and panels are on my extra monitor instead of my laptop where I want them. Anyone know how to fix that? 

Asmoore82 - I'm curious why xrandr doesn't do the trick for me? I would like to be able to set this on the fly (with the panels on the correct desktop as well) an from what I gathered xrandr lets you do that. If I get this fixed I will move on to my other problems which I need resolved before I can use Ubuntu for work. MS VPN connection and getting Likewise to work properly with the domain at work (frustrating problem that one). Then there is of course rewriting all those incompatible excel documents in ooo if possible..

Regards,
Gunnar
Iceland

---

### Post by gr1fter on 2009-08-13
> **Goonie said:**
>  Now my menus and panels are on my extra monitor instead of my laptop where I want them. Anyone know how to fix that? 


all you have to do is right click your panel, choose properties.  uncheck the expand option.  The panel will shink.  Drag the panel to the side of the monitor you want and check back the expand option, it will stick to the new monitor.

Do it again for the bottom (if you have a bottom)

then create a new panel and drag it to the opposite monitor and add the panel "window list"  that will give you the extended taskbar.

Hope that helps and yes...one of my biggest gripe about ubuntu is dual monitor support!

---

### Post by Goonie on 2009-08-14
I managed to get my panels into place (thx gr1fter). but now when I drag windows around I find that a part of my laptop screen is unusable. The extra monitor is on the left of the laptop and f I try to drag a window to the far right of my laptop screen it stops suddenly and can't be dragged further.  I can move my mouse further than the stopped window and interact with the panel functions in the far right corner so the desktop is there, it's just the windows that can't use the entire space. I can't imagine a reason why a window can't be placed on a certain area of a desktop and have not clue what to try next. Maybe try a different distro? Are there any distros more suitable for office use, maybe a non free one? I really would like to use linux at work but this seems like an impossible task. Is this dual monitor problem easier to work out on an nvidia based machine? Or a machine with an Intel vga chip? Will I have to get a new machine to get this to work? 

Regards,
Gunnar
Iceland

---

### Post by gr1fter on 2009-08-14
> **Goonie said:**
> I managed to get my panels into place (thx gr1fter). but now when I drag windows around I find that a part of my laptop screen is unusable. The extra monitor is on the left of the laptop and f I try to drag a window to the far right of my laptop screen it stops suddenly and can't be dragged further.  I can move my mouse further than the stopped window and interact with the panel functions in the far right corner so the desktop is there, it's just the windows that can't use the entire space. I can't imagine a reason why a window can't be placed on a certain area of a desktop and have not clue what to try next. Maybe try a different distro? Are there any distros more suitable for office use, maybe a non free one? I really would like to use linux at work but this seems like an impossible task. Is this dual monitor problem easier to work out on an nvidia based machine? Or a machine with an Intel vga chip? Will I have to get a new machine to get this to work? 

Regards,
Gunnar
Iceland

I believe this site may help with the space issue, even though its referring intel I believe it is all related.

[http://blog.crimm.me/2009/04/ubuntu-904-desktop-affects-cannot-be_27.html](http://blog.crimm.me/2009/04/ubuntu-904-desktop-affects-cannot-be_27.html)

---

### Post by Goonie on 2009-08-14
> **gr1fter said:**
> I believe this site may help with the space issue, even though its referring intel I believe it is all related.

[http://blog.crimm.me/2009/04/ubuntu-904-desktop-affects-cannot-be_27.html](http://blog.crimm.me/2009/04/ubuntu-904-desktop-affects-cannot-be_27.html)
Thx for the link but it didn't help with this particular problem. First of all I don't use compiz at all since dual display was utterly impossible with it enabled and secondly the black area described there is not like my problem since the destkop and icons show up just fine but I can not drag program windows to all places of the screen.. even if the mouse can move to those areas and click icons.

Regards,
Gunnar
Iceland

---

