---
title: "Unity Desktop Resolution/Position Off"
date: 2011-05-04
forum: Desktop Environments
---

### Post by MatthewPlanchard on 2011-05-04
Hi all,

I installed Ubuntu 11.04 today to try it out. I've been using Arch with Gnome3 installed and so far I quite like both of them.

However, I am having a problem with Ubuntu. Since I installed it, the desktop background has only been painted over about 4/5 of the screen. The other portion is black upon login, and after login it just paints with whatever window was in its place prior to switching to the desktop.

It's clearly not a resolution issue, because everything else displays fine. It is also worth noting that it occurs when the panels/unity interface starts. Prior to that, the background covers the entire screen.

I've installed ccsm, and haven't found any settings in there that have fixed the issue.

Any help would be greatly appreciated.

Namaste.


Edit: Okay, in a completely unexplained turn of events, shortly after I posted this, I was browsing GMail when my screen suddenly went black and I was directed to the login window, which was not at the proper resolution (it only filled the center of the screen). From there, I logged in, and the problem was fixed. I restarted to make sure it remained fixed, and it did. I really have no clue what happened, but the problem has been solved.

---

### Post by labrat842 on 2011-05-08
I'm having this problem as well.  After searching high and low, this is the only mention I've seen for it.  Unfortunately, restarting X didn't take care of the issue for me.

I plugged in an external hdmi monitor, and when the resolution reset, it completely borked the screen position/size setting.  it seems like my virtual workspace is set to 800X600, and changing screen resolution does not change this.  The panels go all the way across both monitors, but the desktop ends about 2/3 of the way across my first monitor.

I created a test user account (which I'm posting this from) and it cleared the problem up, so which config file controls this information in Unity on Natty so I can copy it to my old profile?

Thanks in advance!

I've also tried starting unity with --replace and --reset, as well as trying a gdm reset.  Still no dice.  This setting used to live in Xorg.conf, but I don't know where its moved to with unity.

---

### Post by labrat842 on 2011-05-10
Well, I fixed the problem by backing up my home folder and completely reinstalling from scratch, thinking I had screwed up unity's settings attempting to enable desktop cube.

Played my xbox for a while today, went to plug the hdmi of my external monitor into my laptop, once again screen resolution reset, the panels  are fine, but the desktop does not extend to the second monitor, and I can find no way to make it extend.  The usual controls have been moved or removed.

If I create a new user, it looks fine again.

Does anyone know where the virtual desktop settings for unity live now?

short and sweet:  My combined monitor resolutions are greater than my virtual desktop width, and the virtual desktop is not adjusting properly when I adjust resolutions or add a second monitor. 

please don't make me reinstall again!  

screenshots attached.

thanks!

edit:  It appears that workspace switcher sees the desktop as going all the way across the big monitor, and in the correct resolution.  But nothing except the panel is displayed on that monitor, and menus don't display from menu selection on the panel.  Weird.

---

### Post by KittyChunk on 2011-05-16
Same problem here, desktop seems to be mis-aligned and off center, leaving a "hall of mirrors" area between the edge of the desktop background and the launcher (see screenshot). Have tried changing screen resolution, background, restarting X, restarting the machine but nothing seems to fix the problem. This is a fresh install of Ubuntu 11.04 on an HP 2230s laptop with an Intel integrated graphics card. Anyone have any suggestions?

---

