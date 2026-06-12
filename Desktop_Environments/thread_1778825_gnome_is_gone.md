---
title: "gnome is gone"
date: 2011-06-09
forum: Desktop Environments
---

### Post by MSlaveubu on 2011-06-09
Hi,

Ubuntu seems to be screwed up or something.  I was running a game server and a voice chat server on ubuntu 10.10 (I think), the regular edition with gnome.  So everything seemed to stop working, so I restarted, but I could no longer VNC in after several restarts.  SO I hooked up a monitor, and after a while and learning to hit alt + f2 I was able to log in,

BUT it was only in a terminal, black and white no GUI.  I have been able to get my server crap running but I cant do anything else.

HOW do I get the GUI back?  Im thinking maybe my memory went bad and Ubuntu is running in some low memory state?  

I am not, NOT running ubuntu server FYI, regular ubuntu with the gui.  Reason I think it may be the memory is because I cannot run my game server with the 2 gigs of ram I was running it with before, cant allocate enough mem on startup.  

Is that possible?  is it some known issue?  or if not, anyone have any idea?  Im screwed with out the GUI.

Thanks!

---

### Post by pavi_elex on 2011-11-08
sudo apt-get install gdm
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart

---

