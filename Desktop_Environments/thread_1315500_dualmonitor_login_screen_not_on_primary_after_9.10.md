---
title: "dualmonitor login screen not on primary after 9.10 upgrade"
date: 2009-11-05
forum: Desktop Environments
---

### Post by Michael Matthews on 2009-11-05
Upgraded to 9.10. Have 2 monitors, nvidia drivers, 64bit. Gdm login now appears on secondary screen. Was not problem before. Desktop comes up on primary after login. Any ideas how to get gdm to use correct screen?

TIA

Using nvidia twinview.

Solved. Got a new monitor and the problem went away. Have no idea why.

---

### Post by pjbgravely on 2009-11-06
Make sure you have the correct screen set as screen 0 in nvidia-settings. 
If it is hard to tell because you have the same model displays just try switching them.

Paul

---

### Post by rBoLt on 2009-11-06
run your update manager. there is an update for nvidia drivers. maybe it will help.

---

### Post by fcornillie on 2009-11-06
Exactly the same problem here. 2x DELL 2007FP on NVidia card, 64 bit Karmic. 

XOrg in attach.

Thanks.

---

### Post by Michael Matthews on 2009-11-10
I neglected to mention I am running Twinview which treats both screen as continuous space. Therefore there is only 1 screen0 defined in xorg.conf. Obviously, before 9.10 gdm ignored twinview config and just displayed on primary screen now it looks like login treats both screens as a continuous which may seem correct but it is not what I want. I just want twinview for desktop. What a pain.:-(

---

### Post by pjbgravely on 2009-11-10
Try switching monitors to the opposite ports (if you can) and redo twinview for the new positions.

When I tried twinview in the past GDM used both monitors for login but I guess that has changed now.


 Alternately you can try to find where the default screen is specified in GDM. The kernel is probably at fault and calling the wrong port display 0. So much has changed that I have no idea where or what acts for gdm.conf is anymore. 

  Of course messing with configs can make screw up things so you can't even log in so be careful.

Paul

---

### Post by Michael Matthews on 2009-11-13
There is no gdm.conf in /etc/gdm only custom.conf which is apparently what is used now. There is a backup of the old gdm.conf as gdm.conf.dpkg-bak. That could be the problem. 
I see this in old file (among other things):
[servers]
0=Standard device=/dev/console

[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true


[server-Terminal]
name=Terminal server
command=/usr/X11R6/bin/X -br -audit 0 -terminate
flexible=false
handled=false

[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
flexible=false
chooser=true

Anyone know what -audit 0 mean?

---

### Post by benrboone on 2009-11-14
I'm also having this issue where the login screen is on the secondary screen

---

### Post by RossImlach on 2009-11-15
What I am getting is that it is duplicated on both screens. I've not really looked in to how to fix it, but I thought I'd just ask here. If anyone has a solution, it'd be greatly appreciated.

---

### Post by Michael Matthews on 2009-11-16
If you have 2 separate login screens you must not have twinview config but dual x servers for each screen.

I think the issue for me might be gdm config but so far I cannot find any decent documentation for configuring gdm.

---

### Post by LoREZ on 2009-11-25
I'm having the same issue.  Login in the wrong dispaly, and it also makes my e17 use the wrong display for the launchbar.  But in gnome, my panels are in the right display!  Very strange.  Would love to have guidance on how to change settings associated with this behavior.

---

### Post by user39472 on 2009-12-08
Hi, I have the same problem.

Anything new on this? I think I got something. If I during bootup (the dark brown screen with the moving line) move the mouse to the left (my main screen) the login screen appears on the left and if I move it to the right or don't touch the mouse it appears on the wrong screen (right), the mouse seems to start there.

---

### Post by notmyidea on 2009-12-13
Same problem here. Was fine before 9.10.  Anybody found a fix?  I will probably look it into when I got more time over the holidays.

---

### Post by osusoy on 2010-03-26
very, very annoying! pulling my hair out over this ](*,)

and no solutions anywhere just lots of people asking! someone must know how this stuff works! pleeeeaase.

getting very tired of reading the same 'try this' stuff that doesn't work so i'll list what the problem isn't:

- not nvidia or ati specific. people using both have been reporting the same behavior.

- not xorg.conf or what monitor is plugged in where related:
        - the twinview setup works fine once logged in, panels etc all on primary screen
        - any mods to xorg or changing screens that resolve the issue breaks twinview for everything else. any other mods do not have any effect on the problem
        - xsplash displays on the primary, so do boot messages and usplash if turned on etc
        - primary screen gets signal first as it should

- not caused by xsplash; i've tried disabling that in case it was hogging the primary

- the 'login appears where the mouse pointer is' is only partly true; yes, moving the mouse quickly to the primary makes the login 'box' appear there but the rest of the login screen, session options etc, stay on the secondary!

the behavior indicates that gdm powers up primary, powers up secondary and then forgets its now on the secondary and does its business there!

after spending a bunch of time configuring and fixing things wrong with karmic, i'm left with just this one and its driving me nutz...y, its not a functional problem but its just one of those things that eats away at you because there seems to be no solution to something that should be simple!

every other reporting of this problem in forums or bug reports seems to have gotten nowhere but i thought i'll put my own 'mee too' just in case..... ok, back to banging my head against the wall ](*,)

---

### Post by superTP on 2010-08-24
This is still an issue in 10.4.  Does anyone know if it will be fixed in 10.10?

---

### Post by notmyidea on 2010-08-24
> **superTP said:**
> This is still an issue in 10.4.  Does anyone know if it will be fixed in 10.10?

Strangely, the problem has disappeared for me. And funnily enough, I can't remember when it did.  I bought a new widescreen monitor so I am not sure if it went away because of that.  Are you using the Ubuntu NVidia restricted binary or the binary right from NVidia?  I changed to using the (usually) outdated Ubuntu NVidia driver so I am not sure if that is why it works now.

---

