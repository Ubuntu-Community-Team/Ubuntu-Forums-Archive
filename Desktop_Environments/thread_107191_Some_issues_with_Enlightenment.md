---
title: "Some issues with Enlightenment"
date: 2005-12-22
forum: Desktop Environments
---

### Post by Hanj on 2005-12-22
Today I managed to compile E17 from source, and I have been playing around with it for a while. So far, I like what I see, but there are some problems I've ran into:

1. I need some system tray program for programs like Gaim, but I haven't been able to find a good one (I really don't like Engage). I tried wmsystray, but the system icons won't appear in it. Is there some good alternative (or a way to make wmsystray work)?

2. Is there some app for E17 that shows all the running applications? Sort of like the taskbar in Windows. Ibox only shows the ones that are minimized...

3. I installed wmmixer to control sound level, and managed to screw up a little with its borders. I made the window borderless and checked the "Remember settings" box, so that the window is borderless every time I start it. Then I remembered I wanted to make it visible on all workspaces, and now I can't access the border options since there are no borders to right-click on. How to I solve this?

4. This isn't really a big deal, but is there a way to make the dropshadow appear when a window is on top of another window, instead of just over the background? That would look really neat...

---

### Post by Dr. Nick on 2005-12-22
I just did the cvs e17 today aswell.
How did you get engage to run? I dont see it.

For your system tray - Have you considered using e17 and gnome together? You can have e17 running inside of gnome thus giving you the abality to use the gnome tray. Also going this route would give you easier access to the gnome-system-monitor which should work in e17 awelll.

Other than that I dont know of native e17 apps that would accomplish that, but Im just getting started aswell and think it may be easier to integrate e17 with gnome

---

### Post by firecat53 on 2005-12-23
To load Engage:
  enlightenment_remote -module-load engage
  enlightenment_remote -module-enable engage

I had to create a new directory ~/.e/e/applications/engage
and a new file .order within that directory with the list of the .eap files for the icons you wish to include. Once you create that directory, you can also run entangle from the command line to add and remove programs from engage. It's still pretty buggy....

Engage will show most of the programs you have running with a little black carrot under the icon, if there is an icon for that program.  It seems the eap editor file browser is broken right now, as I can't seem to change icons and create new eap's for anything. 

Not sure about the other window-eye-candy features you asked about.

Good luck!

Scott

---

### Post by Hanj on 2005-12-23
Dr Nick: I tried running gnome-panel from E17, and the system tray works, but no windows show up in the window list for some reason.

firecat53: Maybe I should use Engage after all. I can't get the eap maker to either though. 

Btw, Dr Nick, if you installed E17 from source, you will have to download and compile Engage separately. It is located in misc/engage if you use CVS. See [http://www3.get-e.org/EFL_User_Guide/English/_pages/2.1.html](http://www3.get-e.org/EFL_User_Guide/English/_pages/2.1.html).

No ideas about the borderless window? [EDIT]Nevermind, I found out that holding down alt and right-clicking would bring up the window menu.[/EDIT]

[EDIT2]Is there some way to make Engage act only as a system tray? That is, no launch icons and no icons for running apps. Simply making the .order file empty will not get the icons for running apps dissapear.[/EDIT2]

---

