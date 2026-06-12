---
title: "help! i lost my  desktop display setting up compiz"
date: 2009-05-02
forum: General Help
---

### Post by baconrad on 2009-05-02
I just completely <beep> up my desktop display playing with compiz. I'm running easy-peasy 1.1 on an asus eee 1000. I can boot but can't do anything. I initially see a bit of my desktop but the desktop gets covered with black squares as i click. 

How do I restore to some default setting? When I try to boot to recovery mode, i chose terminal with network or something like that and got repeatted msgs trying to unsuccessfully get a network connection.

The last thing I did was run "ccsm", the compiz config settings manager. I cllicked on Disable Effects/Animation when everything started going black. I had also installed compiz-switch and had turned off netbook display mode and was running in whatever the non-netbook mode is called.

I'm new to linux...maybe that's obvious. Thanks for any help. I'm back to the original xandros  installation until I can fix this.

---

### Post by baconrad on 2009-05-02
well, i got a little further but wasn't able to fix the problem. i was able to boot into some backup configuration mode and tried running xfix as well as root. xfix said i had some problems with my configuration and would attempt to fix, but no luck.

so the question at this point is how to get to some workable desktop mode so i can reset to normal netbook mode and start trashing it again

thanks

---

### Post by Cybie257 on 2009-05-02
Well, you can try this method which has helped me in the past with similar issues:

When you can get into a terminal mode (Use recovery and select the terminal mode), type the following:

sudo apt-get remove compiz*

This should list out a bunch of packages related to compiz. Select Y(es) and let it uninstall compiz completely. 

Typing exit after that should bring you back to that menu. If not, reboot and get back to the menu and do the "try to Fix X" option again and continue bot and see if that works. 

This method worked great for me when I tried to install ATI drivers for my card and destroyed my desktop. 

While in the terminal mode, you might want to type the following:

sudo apt-get install ?????-desktop before rebooting just to be sure everything is in tact. At this point, I'm not sure what 'easy peasy' uses for it's desktop packages, otherwise I'd say "gnome-desktop". So, figure out what packages/desktop environment is used. This may not be necessary, but something to try if needed. 

-Cybie

---

### Post by baconrad on 2009-05-02
Yes, that got me back up and running. Now I need to figure out how to switch to back to the standard netbook desktop but that should be doable.

Thanks so much for your help.

---

