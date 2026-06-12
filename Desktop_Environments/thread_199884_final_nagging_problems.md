---
title: "final nagging problems"
date: 2006-06-19
forum: Desktop Environments
---

### Post by jewishj on 2006-06-19
I finally have my system about where I want it, but there are a few more nagging problems I need to take care of - so, here we go, first:

Note: I am using compiz/XGL with Nvidia card/drivers (although not all of the issues are related to this)

1) Since doing the compiz/XGL stuff, ctrl-alt-l no longer works to lock my computer.  I can fix this but I do not know (nor can i find) the command that i can run with a custom keycode.
UPDATE:  Recently using the lock screen option from the menu stopped working too.  After a reboot, and about twenty attempts to lock the screen, it started working again - including the shortcut.  It would seem this is an issue with the lock screen function rather than the shortcut key.
**Fixed: added xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server" - this also fixed an issue with shift+backspace restarting x**

2) Whenever I login to a session, maximizing a window will make the window fill from the bottom of the top panel to the bottom of the screen (going behind the bottom panel).  If I mimimize all windows (or move them out from behind the panel) and then resize the panel and resize it back, then the window will maximize correctly - from the bottom of the top panel to the top of the bottom panel.

3) Even though I have gdesklets set to run on startup (which works fine) the position of the desklets is always moved whenever i logout and recently, after a login, all the desklets were simply gone (even though the daemon was still loaded and working correctly - i could still add new desklets and such).  I do have the "Auto save changes to session" checked from system->prefs->session.

4) Some of the games/screensavers don't operate very well since installing compiz/xgl - I can't tell you which screensavers, but one game is BillardGL.  I know this is a fairly well doucmented issue with openGL games/screensavers, but I have not been able to find a fix in hours of searching on these forums and google, so I was hoping maybe someone else knew if there was a fix and if so what it is.

5) One specific game, Slime Forest ([http://lrnj.com/slimeforest.html)](http://lrnj.com/slimeforest.html)), runs fine in terms of speed and everything, but for some reason the entire window is translucent.. so the only way to really play it is against a black background.  I have uploaded three screenshots to show very clearly what I am talking about.  I have also contacted the developer to see if he knows what's going on or can atleast give me some more technical specs on the game (I will keep this thread updated as I find out more).
**Fixed: The developer gave me a fix**


6) The login screen is half off the top and left of the monitor.  I can use the mouse to move the screen focus over to it, as if the screen space were extended beyond my monitors.  After logging in this problem is fixed (if I logout it will still be fixed, only a reboot will mess it up again).  Note: This always happened since I installed nvidia drivers, even before compiz/xgl.

7) I have a microsoft 6000 laser mouse, and I cannot get the forward/back buttons working in anything but firefox.  I followed the steps I found in various threads here related to that specific mouse, and afterwards the forward/back buttons started to work fine in firefox, but as mentioned, they don't do anything anywhere else.
**Fixed: figured it out using this thread -> [http://ubuntuforums.org/showthread.php?t=44191&highlight=back+forward+nautilus](http://ubuntuforums.org/showthread.php?t=44191&highlight=back+forward+nautilus)**

8 ) I have about six mounted network drives (need to be mounted due to streaming media) and I was wondering how I can add them to the places menu and computer window.  Also is there anyway to edit the default area a browse for file window opens in or to edit the places sidebar in a nautilus window.
**Fixed: found solution at [http://www.ubuntuforums.org/showthread.php?t=145370&highlight=adding+places](http://www.ubuntuforums.org/showthread.php?t=145370&highlight=adding+places)**

Well.. this should cover everything, I will post fixes/solutions as I find them (if they are not answered in this thread) or any new problems that arise.  Thank you to everyone in this community who has helped me get this far.  I could not be happier with the move from windows.

Regards

---

### Post by Indras on 2006-07-02
Let me try to help you out, and I'll describe any problems I'm having as well.  Maybe someone else will come along with more suggestions.

[QUOTE=jewishj]I finally have my system about where I want it, but there are a few more nagging problems I need to take care of - so, here we go, first:

Note: I am using compiz/XGL with Nvidia card/drivers (although not all of the issues are related to this)

1) Since doing the compiz/XGL stuff, ctrl-alt-l no longer works to lock my computer.  I can fix this but I do not know (nor can i find) the command that i can run with a custom keycode.
UPDATE:  Recently using the lock screen option from the menu stopped working too.  After a reboot, and about twenty attempts to lock the screen, it started working again - including the shortcut.  It would seem this is an issue with the lock screen function rather than the shortcut key.[/QUOTE]

I ran into this problem myself recently.  Turns out the screensaver I was trying to use (XMatrix) is incompatible with XGL... the screensaver kept crashing whenever I tried to lock the screen, but of course it gave no output.  I had to run the screensaver manually in a terminal to figure it out.  So naturally, I just switched to GLMatrix instead.  Problem solved.

Also, make sure your computer is loading the correct keyboard layout.  A lot of XGL/Compiz install instructions say to add:

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

to your /usr/bin/thefuture script.  This modmap file is for a 84-key layout.  If you want to have all your keys loaded properly, particularly your windows keys, switch it to 'xmodmap.us-101'

[QUOTE=jewishj]2) Whenever I login to a session, maximizing a window will make the window fill from the bottom of the top panel to the bottom of the screen (going behind the bottom panel).  If I mimimize all windows (or move them out from behind the panel) and then resize the panel and resize it back, then the window will maximize correctly - from the bottom of the top panel to the top of the bottom panel.[/QUOTE]

I've never seen this problem myself.  My biggest problem is that I use the compiz-start.py script to rapidly switch between compiz and metacity, but when I do, I lose the ability to minimize or maximize windows that are currently open, and if I have windows open on multiple desktops, a bunch of programs will crash, rapid-fire, and the script moves them all to workspace 1.

My only workaround for the windows I can't maximize is to right click on the title bar and select "unminimize" first, then the buttons start working again.  But of course, this probably is no help to you.

[QUOTE=jewishj]3) Even though I have gdesklets set to run on startup (which works fine) the position of the desklets is always moved whenever i logout and recently, after a login, all the desklets were simply gone (even though the daemon was still loaded and working correctly - i could still add new desklets and such).  I do have the "Auto save changes to session" checked from system->prefs->session.[/QUOTE]

I personally don't have the auto save changes to session option checked, and yet everything seems to save just fine for me.  I would suggest unchecking it and seeing how the behavior changes.  It might be that it is simply saving your window sizes improperly due to the panel sizes.

On a related note, I installed Starcraft using wine and everything works beautifully, except when I try to run it in full screen 640x480, it doesn't hide the top panel, so it starts the full screen from the bottom of it.  Which means  I lose the bottom 25-30 pixels of the screen.  However, switching to metacity fixes it, so I can't complain too much.

[QUOTE=jewishj]4) Some of the games/screensavers don't operate very well since installing compiz/xgl - I can't tell you which screensavers, but one game is BillardGL.  I know this is a fairly well doucmented issue with openGL games/screensavers, but I have not been able to find a fix in hours of searching on these forums and google, so I was hoping maybe someone else knew if there was a fix and if so what it is.[/QUOTE]

No idea.  I installed a bunch of extra screensavers that I found in Synaptic.  I found many of them won't work in XGL.  And some that do work take 100% CPU usage (like Plasma), which make them totally unusable as a screensaver.

[QUOTE=jewishj]5) One specific game, Slime Forest ([http://lrnj.com/slimeforest.html)](http://lrnj.com/slimeforest.html)), runs fine in terms of speed and everything, but for some reason the entire window is translucent.. so the only way to really play it is against a black background.  I have uploaded three screenshots to show very clearly what I am talking about.  I have also contacted the developer to see if he knows what's going on or can atleast give me some more technical specs on the game (I will keep this thread updated as I find out more).
**Fixed: The developer gave me a fix**[/QUOTE]

Yeah, I had this same problem, except with LOTS of programs.  Running anything in BasiliskII (a macintosh emulator) or DosBox (a DOS emulator) resulted in this behavior.  Also, the Ur-Quan Masters ([http://sc2.sourceforge.net](http://sc2.sourceforge.net)) and Stratagus ([http://stratagus.sourceforge.net](http://stratagus.sourceforge.net)) did this as well.  This is a problem with Compiz, not XGL, since it works just fine with Metacity.  Some programs just naturally allow for semi-transparency and Compiz turns them to full transparency, making the colors bleed through.  The proper fix is to make a script that starts the program, which looks something like this:

```
#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
/name/of/game
```

By exporting that one variable, it forces Compiz to ignore transparency for any applications launched afterwards.

[QUOTE=jewishj]6) The login screen is half off the top and left of the monitor.  I can use the mouse to move the screen focus over to it, as if the screen space were extended beyond my monitors.  After logging in this problem is fixed (if I logout it will still be fixed, only a reboot will mess it up again).[/QUOTE]

That's very odd.  I assume you set up compiz to start with gdm, not with each session, because my login screen was completely unaffected with installing xgl/compiz.  I don't really have any suggestions, sorry.

[QUOTE=jewishj]7) I have a microsoft 6000 laser mouse, and I cannot get the forward/back buttons working in anything but firefox.  I followed the steps I found in various threads here related to that specific mouse, and afterwards the forward/back buttons started to work fine in firefox, but as mentioned, they don't do anything anywhere else.[/QUOTE]

Sorry, I just have a two-button Logitech with a scroll wheel.  Perhaps you'd let me borrow your mouse for a few days to try to reproduce the error? LOL

[QUOTE=jewishj]8 ) I have about six mounted network drives (need to be mounted due to streaming media) and I was wondering how I can add them to the places menu and computer window.  Also is there anyway to edit the default area a browse for file window opens in or to edit the places sidebar in a nautilus window.
**Fixed: found solution at [http://www.ubuntuforums.org/showthread.php?t=145370&highlight=adding+places](http://www.ubuntuforums.org/showthread.php?t=145370&highlight=adding+places)**[/QUOTE]

Cool, thanks for the link.

[QUOTE=jewishj]Well.. this should cover everything, I will post fixes/solutions as I find them (if they are not answered in this thread) or any new problems that arise.  Thank you to everyone in this community who has helped me get this far.  I could not be happier with the move from windows.

Regards[/QUOTE]

---

### Post by jewishj on 2006-07-02
Thanks for the reply.  I had actually not gotten around to updating it in the last week or so, so there were a couple of problems that I fixed that I hadn't updated yet.  Also, the thing with the login screen being off centered happened before installing compiz/xgl, even since I did nvidia drivers.  As for the "auto save to session" option, I had it off, but there would always be a terminal and  nautilus window open whenever i logged in and when I asked how to fix that, I was told to turn that on - which fixed it.  Does anyone know in more detail exactly what that option does.  Perhaps I should close all windows and logout, then log back in and unselect it to get the desired effect?

---

