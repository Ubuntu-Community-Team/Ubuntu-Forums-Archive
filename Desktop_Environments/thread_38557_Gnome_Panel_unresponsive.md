---
title: "Gnome Panel unresponsive"
date: 2005-06-01
forum: Desktop Environments
---

### Post by ChrisHasenpflug on 2005-06-01
](*,)  ](*,)  ](*,) 

Alright, so currently I can see the Gnome Panel...but its not responding to interaction.

How did I get here...

Coming back from the screensaver the panels were gone.  The background for them was there, but no icons or clock or anything.  So I got to a terminal and ran killall gnome-panel.  Alright, all looked normal, but nothing would respond to clicks.

Ctrl-Alt-Backspace

Got the "Panel is already running.  Now exiting" error.  Except panel wasn't there and there wasnt even the background this time.  Fire up terminal again, killall g-p did nothing then i ran gnome-panel and my panel came back.

But again, its not responding to clicks.  The clock is, the active windows area is and I can change virtual desktops.  But the application menu area is not responding to anything so I'm having to start all my apps from the terminal.

Any thoughts??  I've only be running Ubuntu for a few days here now, and its possible that I changed a config to cause this problem.  However, all was fine yesterday when I shut down and I have not changed anything today (except install apache, php and mysql).

Thanks in advance!

---

### Post by neighborlee on 2005-06-01
[QUOTE=ChrisHasenpflug]](*,)  ](*,)  ](*,) 

Alright, so currently I can see the Gnome Panel...but its not responding to interaction.

How did I get here...

Coming back from the screensaver the panels were gone.  The background for them was there, but no icons or clock or anything.  So I got to a terminal and ran killall gnome-panel.  Alright, all looked normal, but nothing would respond to clicks.

Ctrl-Alt-Backspace

Got the "Panel is already running.  Now exiting" error.  Except panel wasn't there and there wasnt even the background this time.  Fire up terminal again, killall g-p did nothing then i ran gnome-panel and my panel came back.

But again, its not responding to clicks.  The clock is, the active windows area is and I can change virtual desktops.  But the application menu area is not responding to anything so I'm having to start all my apps from the terminal.

Any thoughts??  I've only be running Ubuntu for a few days here now, and its possible that I changed a config to cause this problem.  However, all was fine yesterday when I shut down and I have not changed anything today (except install apache, php and mysql).

Thanks in advance![/QUOTE]

----------
no its not you ,,my guess is its some way gnome is interacting with nvidia driver or some component thereof...ati users seem do not have issues and my same driver ( 7174 I think it is ) in windowsXP does n ot give these weird issues you mention, and for which I also have experienced to some  extent.  I have say been running evolution, which crashes and then gnome-panel crashes as does the desktop..one app crashing should not the entire desktop take down ...I had no access to menus on the panel just as you didn't so our stories are similar anyway and Im frustrated too not knowing why or what fix is...if it was memory issues they would consistenly show up in windowsXP by causing similar problems I would think...

if you have an ati card then I guess there goes that theory ;-)

hope someone can fix this nastiness ..

cheers
nl

---

### Post by ChrisHasenpflug on 2005-06-01
[QUOTE=neighborlee]----------
no its not you ,,my guess is its some way gnome is interacting with nvidia driver or some component thereof...ati users seem do not have issues and my same driver ( 7174 I think it is ) in windowsXP does n ot give these weird issues you mention, and for which I also have experienced to some  extent.  I have say been running evolution, which crashes and then gnome-panel crashes as does the desktop..one app crashing should not the entire desktop take down ...I had no access to menus on the panel just as you didn't so our stories are similar anyway and Im frustrated too not knowing why or what fix is...if it was memory issues they would consistenly show up in windowsXP by causing similar problems I would think...

if you have an ati card then I guess there goes that theory ;-)

hope someone can fix this nastiness ..

cheers
nl[/QUOTE]
 its an nvidia card w/ nvidia drivers

---

### Post by neighborlee on 2005-06-01
[QUOTE=ChrisHasenpflug]its an nvidia card w/ nvidia drivers[/QUOTE]

Im not sure what it is frankly, and the few times I asked about this I got no definitive  replies for a cure.

I just know my windowsXP box does not do this nor do the other distros I've tried exhibit this behavior .  I tried getting a top readout when mine did this but I never saw anything, nor in any log files indicating what might be wrong. We can hope that someone replies that has fixed this..;-)

cheers
nl

---

### Post by foo141 on 2008-02-08
In case this helps somebody:

For me the problem was the keyboard layout switching applet (gswitchit). When gnome-panel restarted after "killall gnome-panel", it evidently locked up waiting for the gswitchit applet to initialize. 

Gswitchit is not visible as a process (why?), but you may see an unresponsive window titled gswitchit that Ubuntu lets you kil by pressing close (after a timeout).  After this the gnome-panel comes to life.

---

### Post by foo141 on 2008-02-08
Followup: the processes are named gnome-*-applet. E.g., to kill hung applet(s) from the command line do kill `ps aux | grep gnome-keyboard-applet | awk -- '{print $2}'`

---

### Post by dcra19 on 2008-02-19
I think I can confirm there is something wrong with gswitchit.  I have a Toshiba laptop with an ATI card, etc. 

One day I plugged in a new digital camera to a usb before booting, After I tried loading some pictures via F-Spot, I seemed to have some desktop issues,  I think I just forced a reboot at that point, maybe with the power button (which seems to do a pretty orderly shutdown in Ubuntu.)

After it came back up, for a week I wasn't able to get the gnome desktop to work. Icons would disappear, and come back 10 minutes later.  I made a couple of new accounts for myself which had no problems running Xfce4 (which I am a little familiar with)

I tried deleting all the desktop config directories .gnome, gnome2, .gconf, .gconfd, .metacity.  This would fix it temporarily, and removed some of my customizations.  But the problem would persist over many boots.

On reading your post, I remembered I had had a panel switcher for keyboards, and it had disappeared.  I reinstalled it using the panel customization, and voila!  my desktop seems to be behaving!

What gives with gswitchit and gnome-keyboard-applet?  Anyway, thanks and I will try to remember to let you know if this fixes the problem more permanently.

---

### Post by dcra19 on 2008-02-19
:confused: :mad:

Whoops, that's not it!  Installing the keyboard switcher only fixed it a few minutes, if at all.
Maybe the problem is related, but the desktop is disappearing and some of the panel icons are unresponsive again.

Sorry for the false alarm,

---

