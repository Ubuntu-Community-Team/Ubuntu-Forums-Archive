---
title: "Gnome hangs on 'quit' button"
date: 2008-04-29
forum: Desktop Environments
---

### Post by MaddMatt on 2008-04-29
Hi guys! 
Is anyone else having this problem? 
It started for me in Gusty, which is one of the reasons I stuck to Feisty before fresh installing Hardy. Essentially, when I click the 'quit' button to log out / restart / whatever, GDM hangs. It's not a serious hang, as ctrl+alt+backspace pulls me back out to the login window, but very annoying. Are there any gnome specific logs, or ways of tracking this error? Thanks

---

### Post by sune_cph on 2008-05-01
If you have disabled the power-manager, it's not unusual to see a 30 sec delay or similar before the logout/reboot/shutdown dialog box comes up. I've had this problem for ages (since i always disable the power manager). If i re-enable the power manager, the delay disappears.

/Sune

---

### Post by MaddMatt on 2008-05-07
Great tip - you are correct, the gnome logout screen is simply taking a long time. HOWEVER the power management trick did not work. Any other ideas?

---

### Post by mizar001 on 2008-05-07
Sometimes a background application is still mananaging something and need time to be closed.

Other times applications in other workspaces are in a popup menu (something like : the file has not been saved, do you want to save ?) and those pop up block the shutdown procedure. Usually the mouse will not work in changing workspaces, but you can use ctrl-alt+arrow keys to reach the popup and close it.

Try also to launch shutdown from terminal with '-h now' options and see what happens.

---

### Post by Lambdoid on 2008-05-07
I have the same problem. I have filed a bug report(#223162). Ctrl-Alt-Del doesn't work and causes Gnome to hang. Ctrl-Alt-Backspace works. If I issue sudo shutdown now, the X error console comes up. If I add the -h option, it shuts down fine.

---

### Post by quonsar on 2008-05-07
turning the gnome-power-manager back on solved it for me. i had disabled it.

---

### Post by MaddMatt on 2008-05-07
Which power management are you using? It didn't work for me, but there are two installed apmd and acpid... is there a difference? are they contradicting eachother? 
Thanks,

---

### Post by Ingenium on 2008-05-08
I'm having the same issue. I noticed that it is somehow tied to the power manager. It's enabled for me, but when I switch from battery to AC (or vice versa), the icon sometime disappears. This is when the quit button hangs. Sometimes the power icon will re-appear after a few minutes and then the quit button works fine.

This may be unrelated, but scripts I have set to run on suspend and resume, which worked fine in Gutsy, are not being run.

---

### Post by quonsar on 2008-05-08
> **MaddMatt said:**
> Which power management are you using? It didn't work for me, but there are two installed apmd and acpid... is there a difference? are they contradicting eachother? 
Thanks,

I have both of those enabled in System -> Administration -> Services. But what fixed the hang on quit problem was going to System -> Preferences -> Sessions -> Startup Programs and enabling (or adding) gnome-power-manager. As soon as I did that the log off window started popping up immediately upon hitting quit.

---

### Post by juyanith on 2008-05-08
I have had the same problem since I installed Hardy 64 (beta). At first I just thought it was a beta issue, but it has lingered. Unfortunately, adding gnome-power-manager had no effect. Whenever I shutdown, I have to remember to hit ctrl-alt-del to kill the session or it just hangs. I'm not sure where to look to find out what's causing the problem though.

---

### Post by MaddMatt on 2008-05-09
> **quonsar said:**
> I have both of those enabled in System -> Administration -> Services. But what fixed the hang on quit problem was going to System -> Preferences -> Sessions -> Startup Programs and enabling (or adding) gnome-power-manager. As soon as I did that the log off window started popping up immediately upon hitting quit.

The enabling of gnome-power-manager did it for me! I certainly wouldn't have thought to check sessions for the power manager. Awesome! Thanks!

-Matt

(PS, this is still a bug, as people with desktops shouldn't need power management, no?)

---

### Post by vrybas on 2008-05-10
You could try to shutdown gnome with 
```
gnome-session-save --kill --silent(or without it)
```

and see what's happens

---

### Post by glantucan on 2008-08-12
> **MaddMatt said:**
> The enabling of gnome-power-manager did it for me! I certainly wouldn't have thought to check sessions for the power manager. Awesome! Thanks!

-Matt

(PS, this is still a bug, as people with desktops shouldn't need power management, no?)

Yes, I think so. 
And it's an old and known problem, I found this old post talking about it and giving the same solution:
[http://ubuntuforums.org/showthread.php?t=4037](http://ubuntuforums.org/showthread.php?t=4037)

Anybody knows what the logout menu entry execute? I would like to digg it. I'm trying to put my own script for managing power  together on my laptop, and don't want gnome-power-manager to mess with it.

---

### Post by glantucan on 2008-08-12
> **vrybas said:**
> You could try to shutdown gnome with 
```
gnome-session-save --kill --silent(or without it)
```

and see what's happens

It does have the same delay as the menu entry or applet. Actually it would be really strange if doing different, because they just execute that command. I found it out reading the properties of Session Logout entry under System Tools using Alacarte (sorry for the translation but I use a Spanish version of ubuntu)

I have found something we all may use, anyway.
From [http://bash.cyberciti.biz/desktop/logoff-kdegnome-desktop-user/]("http://bash.cyberciti.biz/desktop/logoff-kdegnome-desktop-user/"):
```
#!/bin/bash
# Script to logoff KDE/Gnome user session.
# With proper permission via sudo it is possible that rest of the users
# can use the same script. You can create Launcher to use this script
# from Linux desktop. Tested on Debian Linux 3.x, but it should work with
# other Linux distros and FreeBSD
# -----------------------------------------------
# Copyright (c) 2005 nixCraft project <http://cyberciti.biz/fb/>
# This script is licensed under GNU GPL version 2.0 or above
# -------------------------------------------------------------------------
# This script is part of nixCraft shell script collection (NSSC)
# Visit http://bash.cyberciti.biz/ for more information.
# -------------------------------------------------------------------------
 
# Bins, adjust them as per your UNIX/Linux/BSD system (default is Debian)
 
PS="/bin/ps"
AWK="/usr/bin/awk"
GREP="/bin/grep"
XARGS="/usr/bin/xargs"
KILL="/bin/kill"
 
# Send HUP signal to X server :)
$PS aux | $GREP X | $GREP -v "grep" | $AWK '{ print $2}' | $XARGS $KILL -HUP $1
```

Name this script as something like gnome-logoff.sh
Change execution rights for all
```

chmod a+x /(whatever the path you saved it to)/gnome-logoff.sh
```
Use it as root
```
sudo /(whatever the path you saved it to)/gnome-logoff.sh
```
The latter is necessary for the killing part. It won't work as a common user.

Hope this helps a bit while this bug is worked out.

Cheers!

---

### Post by Benjamin_Lebsanft on 2008-08-23
It takes 3minutes on my system to show the dialog, thats really annoying, did someone already find a solution, as the power-management-daemon is already running.

---

### Post by 3aTi3 on 2008-08-25
The gnome-power-manager doesn't start for me. I run it in the terminal, and it doesn't write anything, and in the session manager the gnome-power-manager don't show up.

When I tried 'gnome-power-manager --no-daemon', it says:

bata@3ati3:~$ gnome-power-manager --no-daemon

** (gnome-power-manager:8636): WARNING **: This machine is not identified as a laptop.system.formfactor is desktop.

** (gnome-power-manager:8636): WARNING **: This machine is not identified as a laptop.system.formfactor is desktop.
** (gnome-power-manager:8636): DEBUG: This machine is not identified as a laptop.system.formfactor is desktop.
** (gnome-power-manager:8636): DEBUG: We are not a laptop, so not even trying

So the logoff-screen-delay problem still exists. 
Somebody has an idea?

---

### Post by aidave on 2008-08-25
This also happens on my girlfriends computer.  

I had to remove the "Green Running Guy" from the top right panel, so she wouldnt click it and crash everything.  But there is still the "Quit" button in the System menu, which causes the same crash.

---

### Post by thelimey01 on 2008-08-30
I'm having the same problem on Hardy.

gnome power manager runs on startup, and is there if i go to the system monitor.  I've tried disabling and re-enabling it with no success, as well as reinstalling it.

Any ideas? thanks in advance!

---

### Post by 3aTi3 on 2008-09-03
I removed the gnome-power-manager through Synaptic, then the problem disappeared, the logout buttons appeared very quick, but when the next time I launched Ubuntu, it did't start. After login it just stopped loading.

Maybe because synaptic deleted gnome-session with gnome-power-manager, and it's an essential to ubuntu to work.
I had to reinstall it through terminal, then ubuntu loaded, but the original problem still there.

:S

---

### Post by 3aTi3 on 2008-10-18
I reinstalled hardy, and now it works fine.

it was a software incompatibility

---

### Post by chrone on 2009-04-28
i'm having the same problems with ubuntu hardy heron. :(

most of our desktops in office, after being used for around 8 hours or so, the gnome hangs when people tried to hit the power button on the top right of the gnome panel. i need to control+alt+backspace and choose safe xterminal in order to type a command: sudo poweroff. tried to login back with the gnome login session but never worked out, the gnome just hung. :(

i've searched through google and tried the kernel boot option with noapm, noacpi, or both, but it still didn't work out.

my people in office use to have gambas 1, openoffice, firefox, pidgin, and thunderbird, running at office hours. when the time to go home they try to shut the system down and it just hung.

we're experiencing this issue the very start of 8.04 until 8.04.2. almost a year i've been left with questioning how to solve this problem. i could just switch to 9.04, tried this one couple of days and it didn't hang after 8 hours of usage, but it will takes time to upgrade, and rebuild the local repository i've build.

it seems to me the 7.04 feisty fawn is more stable. :confused:

---

### Post by maxpathan on 2009-05-19
I use Hardy 8.04.
Had problem with the long delay when shutdown is clicked.
Fixed it with :

The power manager daemon was unticked.
SYSTEM > PREFERENCES > SESSIONS > STARTUP PROGRAMS. Scroll down and tick Power Manager

---

### Post by chrone on 2009-05-19
thanks for the reply, i've waited over 1 hour but the long delay seems keep hang there. *shrugs

i'll try with your suggestion to the left over machine in ubuntu 8.04. i have reinstalled some of the machines to 9.04 since 9.04 didn't have this symptom.

---

### Post by chrone on 2009-05-28
somehow it finally stops hang on quit after i change all the setting in sound from pulseaudio to alsa.

disable, restart, and re-enable the power manager in the system > preference > session > start up.

i also change the pidgin sound preferences from pulseaudio to alsa since it sometimes crashes while using yahoo messenger.

for now the system is quite responding to restart and shutdown though after using openoffice 2.4.1, gambas 1.0.18, pidgin, and firefox 3.10 in a long 8 hours straight. hope this normal situation will continue for last.

---

