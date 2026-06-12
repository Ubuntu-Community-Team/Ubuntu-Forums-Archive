---
title: "Gnome Shell Won't Start (13.04 Gnome w/3.8)"
date: 2013-06-01
forum: Desktop Environments
---

### Post by kendoori on 2013-06-01
I am running 13.04 Gnome version with 3.8. All was running fine until today when I tried to install the Intel Graphics driver installer. I also made a tweak because of issues with Citrix icaclient. I definitely broke something here.

When I start the machine I do get a login; however, it is showing the default Gnome login wallpaper and everything is very large. If I put my login credentials I get to a desktop with the default Gnome wallpaper but nothing else. The cursor shows as a large X.

I can SSH into the machine and removed the Citrix client, and also the Intel drivers that I installed. I rebooted, but no go. No desktop.

I have also run: sudo apt-get dist-upgrade

What's best next step here?

---

### Post by converted on 2013-06-01
Exactly the same problem when I decided to try out 13.04 Gnome in a VM today.  (For the express purpose of seeing what extensions would still be available to me after upgrading to 3.8 + making sure such an upgrade would go smoothly)

I thought it had something to do with running in Virtualbox.

Sorry I have no solution...  :-)

---

### Post by kendoori on 2013-06-01
It seemed that the various events that led up to this Gnome-shell login issue (there was an error regarding a partial-upgrade somewhere in there) had some uninstalled Gnome-shell. I reinstalled and it seems that I'm mostly back to normal. Am having an issue with my external display not switching properly at startup, but I appear most of the way there.

---

### Post by markbl on 2013-06-02
I am running stock Ubuntu 13.04 x64 + gnome-shell + gnome 3 ppa and something odd occurred with the package updates today on that combination. Ubuntu software update popped up yesterday and today with a "partial upgrade" message so I cancelled it. I ran aptitude and it wanted to delete a heap of packages, including gnome-shell. I stepped through all/most of the aptitude resolution options but all wanted to remove a heap of packages. I then ran synaptic and it upgraded a few things. I rebooted, and then all package managers were happy and showed everything up to date, including gnome-shell running as normal.

Apart from all that, I have picked up a really annoying google chrome bug since yesterday. Gnome seems to now start two instances of chrome so I get "can not open your session" popups from chrome. I will go and chase where that is coming from now ...

---

### Post by markbl on 2013-06-02
BTW OP kendoori, I also installed that garbage intel driver installer software which was posted in the last few days on webupd8. Apart from the obvious flaws in that program, it also caused one of my 2 screens to frequently go blank. I removed libva-intel-vaapi-driver and i965-va-driver packages and my system returned to normal.

---

### Post by jaweinre on 2013-06-04
Avoid the intel driver installer crap, it's still on diapers. Really, you should upgrade video drivers only if there's stuff you read on changelogs and explicitily need.
Btw the partial upgrade issue has been resolved and it's safe to update now.

---

### Post by Cheesemill on 2013-06-04
Also 13.04 already comes with a later Intel driver than the one offered by their update tool (2.21.6 vs 2.21.3) making the whole thing pointless.

[http://packages.ubuntu.com/search?keywords=xserver-xorg-video-intel&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=xserver-xorg-video-intel&searchon=names&exact=1&suite=all&section=all)
[https://01.org/linuxgraphics/downloads/2013/2013q1-intel-graphics-stack-release](https://01.org/linuxgraphics/downloads/2013/2013q1-intel-graphics-stack-release)

---

### Post by kendoori on 2013-06-04
@Cheesemill thanks on that. The whole Intel driver upgrade was pointless and regretful. 

BTW, incase anyone else is having issues with external monitor switching when docked, I was able to successfully get 13.04 to recognize my docked (or undocked) state video wise and display the correct monitor (LVDS vs. DP2 in my case) and login to the right display using: [https://github.com/wertarbyte/autorandr](https://github.com/wertarbyte/autorandr) I just put the script in my startup applications.

autorandr --change --default mobile

---

