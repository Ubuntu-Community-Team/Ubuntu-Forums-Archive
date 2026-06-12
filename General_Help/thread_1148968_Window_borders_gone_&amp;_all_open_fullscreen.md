---
title: "Window borders gone &amp; all open fullscreen"
date: 2009-05-04
forum: General Help
---

### Post by eekfonky on 2009-05-04
Hello
Having recently upgraded to ubuntu 9.04 64 bit desktop. My window borders are missing and all my windows open fullscreen. Both of these things are very annoying, I often use multiple open windows and like to control the size of them. Please help

---

### Post by garythegoth on 2009-05-04
> **eekfonky said:**
> Hello
Having recently upgraded to ubuntu 9.04 64 bit desktop. My window borders are missing and all my windows open fullscreen. Both of these things are very annoying, I often use multiple open windows and like to control the size of them. Please help

Where you using Emerald before?

---

### Post by eekfonky on 2009-05-04
No I wasn't emerald doesn't work, I've installed it to no avail. I've uninstalled it but it doesn't help.

---

### Post by garythegoth on 2009-05-04
> **eekfonky said:**
> No I wasn't emerald doesn't work, I've installed it to no avail. I've uninstalled it but it doesn't help.

Okkkkkkkkkkkkkkkkkkkkkkkk..............

Umm this maybe stupid but try pressing F11 a few times, see what happens.....

---

### Post by 4Orbs on 2009-05-04
This is based on "how I got it to work".
1. Turn off the visual effects at System-> Preferences-> Appearance, then
2. That should have brought back the window borders. Then...
3. Set your screen resolution back to "Default" or "Auto", then...
4. Re-enable the visual effects. Then...
5. If you now have the window borders and visual effects, this means that...
6. In order to keep the window borders while visual effects are enabled, you will need to change screen resolution by editing the xorg.conf file instead of using the screen configuration gui.

---

### Post by garythegoth on 2009-05-04
> **4Orbs said:**
> This is based on "how I got it to work".
1. Turn off the visual effects at System-> Preferences-> Appearance, then
2. That should have brought back the window borders. Then...
3. Set your screen resolution back to "Default" or "Auto", then...
4. Re-enable the visual effects. Then...
5. If you now have the window borders and visual effects, this means that...
6. In order to keep the window borders while visual effects are enabled, you will need to change screen resolution by editing the xorg.conf file instead of using the screen configuration gui.

Dude if he didnt have Emerald enabled, i doubt that will help....

---

### Post by eekfonky on 2009-05-04
Aye, that didn't work either. Thanks for trying

---

### Post by 4Orbs on 2009-05-04
Did the window borders reappear when you turned off the effects?

---

### Post by eekfonky on 2009-05-04
No they didn't I'm afraid

---

### Post by 4Orbs on 2009-05-04
Another quick test. Turn the effects off. Log out and at the login screen click Sessions and select Gnome Session instead of Last Session. Log in. Are the window borders there now?

---

### Post by eekfonky on 2009-05-04
still no joy. That didn't work either

---

### Post by 4Orbs on 2009-05-04
Do you have the compizconfig-settings-manager installed? If not, to make things easier, you can install it with Synaptic.

---

### Post by eekfonky on 2009-05-04
I do have it installed, now what?

---

### Post by 4Orbs on 2009-05-04
Open the Compiz Config Mgr from the System-> Preferences menu, go down to the Effects section and click on the Window Decoration button to open up the options, then look at the Command. It should be /usr/bin/compiz-decorator. If not, replace the command with the above, log out and back in and hopefully things will have changed for the better.

---

### Post by eekfonky on 2009-05-05
Changed that, logged out and back in, still the same though - curses!
See attached to see how the folders open fullscreen and without borders, firefox and evolution do the same.

---

### Post by soro2005 on 2009-05-05
Hold the <alt> key and pull the window downward with your mouse until it detaches from screen margin. Your video setup is fine, and you have window borders. The window has just slipped underneath the gnome panel.

---

### Post by 4Orbs on 2009-05-05
You have the options of installing fusion-icon from Synaptic, and using it to easily test different combinations of window manager and decorator...

Or you can try this first. Look in your personal Home folder, and from the View menu select to show hidden files. If you have a .emerald folder, delete it. Turn off the desktop effects. Then open a terminal and enter metacity --replace &

Reboot. At the login screen choose Gnome session (just for this session). Login.

Am I correct in assuming you have no window borders on all windows. Including small dialog boxes and such?

---

### Post by wersdaluv on 2009-05-05
Run metacity on the terminal and post the output here if there is

---

### Post by eekfonky on 2009-05-05
Ok, if I hold down alt and drag the window it pops back into shape. i.e. the windows like a terminal go back to the correct size with borders and all others do the same. However if I open them up again the same problem occurs. Is there a way to get the windows to open up correctly every time?

Thanks guys

---

### Post by soro2005 on 2009-05-05
Hmm, good question. If you have the full CompizConfig Settings Manager installed, there is an option "Legacy Fullscreen Support" under "Workarounds." Try toggling that one.

Or perhaps, you can throw away all your compiz configuration and start over with a fresh one:
```
rm -r ~/.config/compiz
```

Log out and log back in.

To see whether it's really compiz, or perhaps the window decorator, hit <alt>+f2 and type
```
metacity --replace
```

Will be reverted to your normal session if you log out and log in again.

---

### Post by soro2005 on 2009-05-05
If it's only the Nautilus windows that are stuck underneath the Gnome panel, this might help: Run nautilus from a terminal like this
```
nautilus --geometry=400x300
```
Resize it to a normal window size. Close it, and see whether it remembers its geometry.

---

### Post by giancast on 2009-05-05
I had the same/similar issue yesterday. My windows opened fine, not full screen, but I did not have the minimize, maximize or close buttons at the top, neither the File, Edit, etc. buttons. So I disable Compiz and all the effects, went back to None and all the windows were fine. Then re-enabled Compiz and the top portion of the windows were back.

---

### Post by eekfonky on 2009-05-05
None of that worked either

---

### Post by eekfonky on 2009-05-06
Anyone? This is really doing my head in. I need to hold alt + left mouse and drag the windows. when I get the top taskbar for minimise etc. I hit maximise and the windows expand under the top and bottom taskbars. All windows when opened do the same. Can anyone help?

---

### Post by 4Orbs on 2009-05-06
Something to try: right click on the top or bottom panel, select properties and choose auto-hide the panel, then a few minutes later deactivate the auto-hide panel. That might reset the window geometry.

---

### Post by eekfonky on 2009-05-06
When i do that the window just expands to fill the gap. See screenshot below

---

### Post by dragos240 on 2009-05-06
Try Alt+F2 and type "metacity".

---

### Post by eekfonky on 2009-05-06
No change. sorry

---

### Post by 4Orbs on 2009-05-06
Are you able to resize the windows by dragging from the corner inward?

---

### Post by eekfonky on 2009-05-07
Only after I hold down Alt and drag the window top bar into sight. But the resize never stays. As soon as I close it down and reopen it same problem.

---

### Post by 4Orbs on 2009-05-08
Don't know if these might help. I know you have tried some of this before, but not in the sequence below.
1. Open Synaptic Package Mrg. and in the lower left menu click on status. See if there are any residual files left from when you had Emerald installed. If so, mark them for complete removal then hit the Apply button at the top.
2. In the System-> Preferences-> Startup Applications gui, go to Options and Un-check the "remember running applications" option.
3. Turn off desktop effects in System-> Preferences-> Appearance-> Visual Effects.
4. Reboot. Login.

If that doesn't fix it, then I suggest opening the Users and Groups from the System Admin menu and create a new user, then log in to the new users account and see if the window problem exists there also. I'm betting the new users windows will be fine. Meaning that the problem is only in your personal configuration files somewhere.

---

### Post by eekfonky on 2009-05-08
None of that worked and the created new user had the same window problems. sorry

---

### Post by 4Orbs on 2009-05-08
Wow, what a drag. Seeing as how the new user account does the same thing, I would guess it is somehow connected to the screen resolution and graphics driver. You might try different resolutions and refresh rates, but that could break the driver and force you into low graphics mode. I don't recall ever seeing a full screen mode option anywhere in the settings of the browser, metacity or nautilus... but it seems that could be what is happening also.

When did this quirk begin? Did it start when you were experimenting with Emerald?

If you right-click on a window title bar, you have an option for "Always on Top". That should keep the window above the panels rather than hidden behind them. Does that work correctly?

---

### Post by eekfonky on 2009-05-08
I installed emerald but never used it. It's now uninstalled.
When I make the windows 'always on top' still no difference....This is seriously annoying!!! Thank you for trying though

---

### Post by 4Orbs on 2009-05-08
Sooner or later someone will post a suggestion that you do a fresh install of Ubuntu. But I think it can be fixed without re-installing. I just don't know how. I'll keep an eye on this thread although I'm out of ideas (for now). Good luck.

---

### Post by soro2005 on 2009-05-08
So this might be a problem of a faulty configuration of screen resolutions then. Have you ever manipulated your xorg.conf? Can you post the contents of /etc/X11/xorg.conf?

What I find weird is that your windows don't remember if they've been closed in a state other than fullscreen. You could open gconf-editor and search whether you find a suitable key in the Metacity section. Also, did you try to install and run xfce? What happens there?

*Edit: Also this might be for you: [http://www.linuxquestions.org/questions/linux-software-2/trouble-with-window-position-559754/](http://www.linuxquestions.org/questions/linux-software-2/trouble-with-window-position-559754/)
This is on the assumption that Compiz is the culprit, which may not be the case. But just in case, make sure you have "smart" selected as "Placement Mode" in the "Place" plugin of Compiz, and also, in the General section of the Compiz Manager, go into the Display Settings tab and make sure it all looks sound (mainly the Output resolution and the Overlap handling). Again, that's Compiz, which doesn't seem to be the problem. Just in case.*

---

### Post by eekfonky on 2009-05-10
Is it possible to re-install the original graphics etc. from the live cd without a fresh install?

---

### Post by soro2005 on 2009-05-11
Normally, there is not much to be installed there. It's just the configuration of the graphics server (x-server) that might be faulty. You can try to fix it by booting into recovery mode and running xfix. Or you log out, change to a virtual terminal, and issue
```
sudo dpkg-reconfigure xserver-xorg
```
I think that has the same effect, although it might be a little more hands on than xfix. You will be asked a series of questions to which you'd probably best respond by hitting <return>. This is supposed to be reasonably fool proof, but there's a chance that you end up without a usable graphics configuration. I'd recommend you back up the file /etc/X11/xorg.conf before you do that. Supposedly, you end up with the graphics configuration you would have gotten from a clean install. So before you trash your entire installation, you may want to try this. You can also open synaptic and select reinstall for the package xserver-xorg and the xorg package that corresponds with your graphics card.

---

### Post by eekfonky on 2009-05-11
I tried to reconfigure the xorg, but all I get with that command are keyboard options. I'll try the other suggestion and let you know

---

### Post by eekfonky on 2009-05-11
How do i use xfix? I have dual-boot OS so do i do it at the grub menu? The rest doesn't work - this is so annoying!! But thanks for the help

---

### Post by soro2005 on 2009-05-11
I've never seen xfix in the wild, but according to what I read, you start your machine into recovery mode (should be an option in the grub menu, underneath each of the kernels which you have installed). You then get a new menu which offers you to try to fix the x server with xfix. According to what I understand, it does the same as dpkg-reconfigure xorg-xserver, but there might be some wrapping script that passes on some Ubuntu specific variables to make it easier. Not sure.

To make sure that this even normally works with your graphics card, have you booted the machine from a live cd? Do you get the same problem?

Also, you could just open the x-server configuration file and paste it here, for us to inspect:
```
gedit /etc/X11/xorg.conf
```

Finally, post the output of
```
lspci | grep VGA
```

---

### Post by eekfonky on 2009-05-11
Sorry I got sick of it and did a fresh install. I have a lot of work to do and don't have time to drag and resize each window. Thanks for the help though.

---

