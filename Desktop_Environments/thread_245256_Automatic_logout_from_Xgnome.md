---
title: "Automatic logout from X/gnome"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Aelfrick on 2006-08-27
This should be an easy one, but I can't find any information on my problen, so let me lay it out here. I have Power Management set to put the monitor only to sleep after 20 minutes, after which I have to relogin each time to my gnome session. I would like to cancel this automatic logout, but I can't find any option for it within the menus, nor online. The only automatic logout I see is using the "TMOUT" option within /etc/profile, which isn't set. The weird thing is that this is my 3rd Dapper install, and this is the only box that has ever automatically logged me out of anything. Any thoughts?

Athlon 64 3700+
LanParty UT nF3 250Gb motherboard
1024M DDR400
various IDE and SATA hds
Geforce 6800 512M
Dapper with gnome/XGL/compiz

---

### Post by lagagnon on 2006-08-27
Are you sure you're not talking about the "Lock Screen" facility which just asks for your password when your monitor has gone into standby? If that is the case change that under System, Preferences, Screensaver, Lock Screen....otherwise I can't help you.

---

### Post by Aelfrick on 2006-08-28
No, it's not a screen lock as from the screensaver options, it logs me out of my gnome session, and when I log in, it always starts with a nautilus browser in my home directory, and nothing else that was previously running is shown. I always have gkrellm on my desktop, and while the process is still in the process list, it doesn't show on the desktop. That same is true of any program running while the system logs me out of the previous session.

<edit>
So after playing around a bit more, some programs are killed  when I am forcefully logged out (firefox is the only one so far), I always have a nautilus browser that pops up, which is always set to my home directory, a gnome terminal has popped up the last 3 times, and gkrellm... well, some times it is shown, some times is it running (according to ps), but isn't on the desktop. If gkrellm is shown on the desktop when I log back in, gkrellm also shows up on the taskbar and switcher, even though I have the options set (which are still checked) not to view gkrellm on either. Also, amarok seems to come back every time, although it shows the window when I always minimize the program to the panel. Any bittorrents (using default bittorrent client) are also killed when I get logged off. You can imagine how this might affect what is otherwise a fully functining system.

Help me Ubuntu-Wan, you're my only hope!
</edit>

---

### Post by protaginist on 2006-11-03
I posted a reply to another person having a similar problem. My system started doing the same thing several days ago for no apparent reason. As a temporary solution try unchecking Activate Screensaver When Idle under System-Preferences-Screensaver and see if that fixes the problem.

This worked for me, but don't ask me why. It should not affect the system in this manner. When I have time i am going to dig a bit deeper. I can't swear to it, but I think this started right after I installed my updates earlier this week so I am wondering if one of then changed something. Anyway, let me know if this works for you as well.

Bill

---

### Post by Thaurwylth on 2006-12-01
I believe this is a bug and should be reported. It appears to be due to screensaver starting up. I recently updated from Debian to Ubuntu Edgy Eft. For some time now my computer always, or next to always logged me off from Gnome after 10 minutes of idle time. This is exactly my screensaver time limit. I disabled screensaver and also disabled monitor power saving mode and now everything seems to be fine. I no longer get logged off from Gnome randomly.

-- Matti Nuortio, Oulu, Finland

---

### Post by DavidVanCan on 2006-12-01
I also think the problem is with the screensaver. When I have the screensaver set to turn on when the computer is idle for 10 mins, the screensaver turns on as it is supposed to but, about 10 additional minutes later, I lose my Gnome session and have to log back in.

I have:
1) Turned off all the "Power Management" preferences
2) Made sure my BIOS has power management features turned off
3) Commented out Option "DPMS" from xorg.conf

When I turn OFF the screensaver I don't lose the Gnome session.

Ubuntu 6.10, Desktop-i386

---

### Post by coralsaw on 2007-02-02
Bumping this one.

(..and a warm hello to all, just moved house to Ubuntu via a longtime gentoo->debian path and a 2mo trial of Edgy).

I have the same issue. Does anyone know if a bug has been filed? Could you pls point me to the bug logger for Ubuntu so I can check myself.

TiA

---

### Post by Bpabreu on 2008-04-23
I did not test it yet, but it seems, as I see in [_[COLOR="Blue"]another topic[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=355607"), that: 

> gnome-screensaver resets every 10 minutes as part of the random selection - even if random isn't chosen. We need to change that to a larger number, otherwise nothing will render or download properly.

Presumably it is this reset of screensaver what is causing the crash of X-window. So, when I get my hands on my computer, late afternoon I will, as suggest, write in terminal the follow:


```
gconftool-2 --type int --set /apps/gnome-screensaver/cycle-delay 100000
```

As I said, I will try this solution this afternoon, dont know yet if it works.

---

