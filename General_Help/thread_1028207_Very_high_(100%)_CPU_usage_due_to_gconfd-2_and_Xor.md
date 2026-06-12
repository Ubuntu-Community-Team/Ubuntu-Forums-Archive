---
title: "Very high (100%) CPU usage due to gconfd-2 and Xorg"
date: 2009-01-02
forum: General Help
---

### Post by kukiszabolcs on 2009-01-02
Hello,

I'm rather new to Ubuntu, I've installed Ubuntu 8.10.
I installed and un-installed compiz, also the proprietary ATI Drivers and now I'm seeing 100% CPU usage in the system monitor applet.

Top looks like this:
```

top - 13:04:00 up  1:27,  1 user,  load average: 2.35, 2.62, 2.80
Tasks: 145 total,   7 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s): 65.8%us, 34.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1552664k total,  1517456k used,    35208k free,   311988k buffers
Swap:   976552k total,     5164k used,   971388k free,   560232k cached

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
27017 k         20   0  7840 4856 2200 R 19.8  0.3   7:58.87 gconfd-2
26825 root      20   0  305m 103m  10m R 14.1  6.8   8:31.72 Xorg
27473 k         20   0 41816  22m  13m R  8.9  1.5   4:11.20 gnome-system-mo
29147 k         20   0  303m 166m  25m R  8.9 11.0   3:31.69 firefox
27224 k         20   0 15812 6184 4508 S  3.0  0.4   1:01.29 magnifier
27000 k         20   0  9512 7736  848 S  2.0  0.5   0:51.34 dbus-daemon
26878 k         20   0 24764 5780 4656 S  1.7  0.4   0:41.15 x-session-manag
13397 k         20   0  122m  26m  15m R  1.0  1.7   0:06.20 konsole
27112 k         20   0 21244 3804 2504 S  1.0  0.2   0:19.90 gnome-screensav
 5701 k         20   0 87164  37m  15m S  0.7  2.5   0:15.42 skype
 9878 k         20   0 35736 9536 8240 S  0.5  0.6   0:01.82 klauncher
 9883 k         20   0 58732 9992 7616 S  0.5  0.6   0:02.50 kded4
 9901 k         20   0 49176 8364 6912 S  0.5  0.5   0:02.56 knotify4
17878 k         20   0  2416 1180  892 R  0.5  0.1   0:00.02 top
18200 k         20   0 15068 4704 3856 R  0.5  0.3   0:00.02 metacity
27026 k         20   0  5688 2192 1824 S  0.5  0.1   0:03.02 gvfsd
27126 k         20   0 46860  22m  13m S  0.5  1.5   0:12.16 gnome-panel
27209 k         20   0 25484  12m 7368 S  0.5  0.8   0:19.14 python
27218 k         20   0 28024  15m 9216 S  0.5  1.1   0:04.06 update-notifier
    1 root      20   0  3056 1888  564 S  0.0  0.1   0:01.38 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify

```

Can anyone help me with this?
My problem is that sometimes the system is not very responsive and I think this is why.

Also I tried to kill gconfd-2 but it re-spawns every time, so no much luck with that.

Thank You Very Much in Advance!

---

### Post by laceration on 2009-01-02
That is normal for Xorg.  Xorg does a lot stuff like making all the windows, etc.  My gconfd-2 doesn't even show up when I do a $top.  I think that is your problem.  

Why don't you try logging out ( ctrl + alt + backspace) then at the login screen before you log in click choose session and select failsafe gnome.  Once you have entered your gnome session open a terminal and do another $top.

If you no longer have gconfd-2 using up all that cpu it would indicate you have a bad gnome configuration.  If that is the problem wipe out your gnome configuration by deleting your .gconf, .gconfd, .gnome and .gnome2  directories.  They are in your home directory. I wouldn't delete them at first though, just in case, I would just rename them.

Doing this, you loose all your gnome settings and have to redo them all.  A pain, but in your case worth it, I think.

After renaming, logout and back into a normal gnome session.  New .gconf +.gnome dirs will be generated.

Also do not leave the gnome-system-monitor open if you are not using it--it uses up a lot of cpu.

---

### Post by etamax on 2009-01-03
I have the same problem here. I have tried logging using the failsafe Gnome but the problem persists.
My gconfd-2 can reach even 30% of CPU usage.

Even deleting .gconf, .gconfd, .gnome and .gnome2, gconfd-2 goes to 30%

I think that the problem is related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/293535](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/293535)

but any solution for the moment...

---

### Post by kitara on 2009-01-04
I am also having this issue. Thanks for pointing to that other thread.  I will be watching both places to see if there is a fix. I have only been using this ubuntu install (netbook remix and metacity) for 10 days and this only popped up recently.  My processor cannot handle this kind of load!

---

### Post by burrobad on 2009-04-18
Hi, nice to see this thread here.. 

For me worked to remove metacity from autostart applications - this was there due to previously not starting metacity, but obviously some updates had corrected this issue, and then it led to high gconfd-2 load.
now it works flawlessly for me..

Regards,

burrobad

---

### Post by isparkes on 2009-04-18
> **kukiszabolcs said:**
> I'm seeing 100% CPU usage in the system monitor applet.

The system monitor applet is a heavy user of the system resources, especially if you have a large screen (I think it's something to do with the smooth scrolling, but that's just a guess).

I remember that I had this problem, but it went away itself.

Anyhow, top is a much more reliable tool for checking CPU usage.

---

### Post by fjpos on 2009-05-04
Hi,


I had a similar problem after upgrading to 9.04 Jaunty and eventaully found by shutting down or removing the
"vino-server" which is part of the gnome remote desktop connection everthing went back to norm CPU usage 1%-4% from a constant 35%


sudo apt-get remove vino-server

or you can just stop it without removing


Good luck

---

### Post by HeadHunter00 on 2010-03-27
I confirm that this problem exists in arch linux as well.

EDIT: I solved it by reinstalling fusion-icon

---

### Post by HeadHunter00 on 2010-03-27
Its sad for windows users that they experience it everyday and think this type of problem is normal. Whereas for us, linux users, it's the biggest bug in the universe.;)

---

### Post by scatha on 2010-04-21
Hi! i had similar problem, and found this thread- first i tried to rename (=delete) ~/.gconf and ~/.gconf2 .. no success.. after i renamed ~/.gnome and ~/.gnome2 it worked again! thanks for help!

---

### Post by cheeseburgerman1 on 2010-06-16
Im having this same problem. Gconfd-2 started leaves idle processor at 66-77 percent, gconfd-2 stopped brings it down to 22 or so percent. I would also like to state that i run Windows 7 on this machine and its idle processor speeds go down to 0-4 percent. So please, dont act like us windows users deal with this daily.

---

### Post by Elmer Fudd on 2010-07-10
> **burrobad said:**
> Hi, nice to see this thread here.. 

For me worked to remove metacity from autostart applications - this was there due to previously not starting metacity, but obviously some updates had corrected this issue, and then it led to high gconfd-2 load.
now it works flawlessly for me..

Regards,

burrobad

I played around with all sorts of attempts to kill,stop,end the offending gconfd-2 process until I also remembered that I had to force metacity on to fix an earlier problem.  Disabling it in Startup (system/preferences/startup applications) fixed it (with reboot). So it is solved for me.

Lucid 2.6.32-23 generic pae
Gnome 2.30.2

---

### Post by nardis_Miles1 on 2010-07-26
I had fixed this issue by removing metacity from my startups. It's still not there, but now, after a couple of updates, metacity is constantly restarted, as evidenced by repeated commands

ps -ax | grep meta

and by the constant updating of the file %gconf.xml in the directory

/home/user/.gconf/applications/window_manager

Also I had removed the directory

/home/user/.gconf/applications/metacity

but it has been regenerated.

Before I start mindlessly to remove directories, I'd like to ask a couple of questions:

1. What, besides the autostart menu, starts metacity?
2. What window manager runs the login menu?

Art Edwards

---

### Post by nardis_Miles1 on 2010-07-27
So, I have finally been able to reduce to a negligible level the gconfd-2 cpu usage. It turns out that the policy kit authentication agent was the culprit. I don't completely understand its function. The command that starts it is

/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1

I'm running gnome, although kde is installed on the box as well. I'm guessing that in my KDE configuration, I am still using metacity. That would account for the persistent attempts to start this wm. 

To finish this solution, it turns out that there is another polkit tool for gnome. I have substituted


/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

Now I have negligible persistent cpu usage. You have to match the policy kit tool to the desktop environment.:)
This may help others who are still facing the gconfd-2 problem.

---

### Post by xiboce on 2010-09-07
workaround:

[http://ubuntuforums.org/showthread.php?p=9815898#post9815898](http://ubuntuforums.org/showthread.php?p=9815898#post9815898)

---

### Post by nsk7even on 2011-03-30
Hi, I just want to drop a few words because for me the problem originated from the desktop symbols for computer and personal folder I activated via Ubuntu Tweak.
But to confuse this, the silly high CPU load occurred only after restart of the system. And it disappeared only after restart as well..

So maybe s. o. else has activated those icons as well? I havent tried if manually placed starters/shortcuts/folders/files provoked the same weird behaviour.

---

### Post by jmw86069 on 2011-06-20
A decent way to troubleshoot the problem is to check the file "~/.xsession-errors".  If symptoms are similar to those in this thread, the file will be many hundreds of megabytes in size!

For me the error was something like this:
"DEBUG: GsmAutostartApp: starting gnome-wm.desktop: command=gnome-wm"

The issue was caused by gconf calling "gnome-wm" instead of a specific window manager.  In the man page for gnome-wm, it states that in absence of a specific window manager, it will pick one from the .config/ directory.  And if you're reading this thread, it's quite likely it chose incorrectly.

I opened gconf-editor, desktop/gnome/session/required_components, and changed windowmanager from "gnome-wm" to "metacity --replace". I tried "metacity" but it didn't resolve the problem. The "--replace" fixed it immediately. No reboot necessary.

I suspect gnome-wm simply needs to add "--replace" to its vernacular.

---

