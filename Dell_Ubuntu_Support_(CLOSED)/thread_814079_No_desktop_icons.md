---
title: "No desktop icons"
date: 2008-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sparkguitar05 on 2008-05-31
Occasionally when I boot into Ubuntu it loads without any desktop icons.  This gets REALLY annoying after a while.  Anyone know how to fix this?

---

### Post by sparkguitar05 on 2008-05-31
*bump*

Anyone?  This is driving me nuts.

---

### Post by prshah on 2008-05-31
> **sparkguitar05 said:**
> Occasionally when I boot into Ubuntu it loads without any desktop icons.  This gets REALLY annoying after a while.  Anyone know how to fix this?

Which icons are you missing? If the missing icons are NTFS/FAT32 drives, then these are not automatically mounted after a bad shutdown.

The next time this happens, can you post a screenshot? How do your recover from this situation... restart?

---

### Post by sparkguitar05 on 2008-05-31
All the icons are gone.  The drives are gone.  The programs are gone.  The files are gone.  And I cannot right-click on the desktop.  I can recover from this by restarting the computer.  I will post a screenshot next time it happens.

---

### Post by prshah on 2008-05-31
> **sparkguitar05 said:**
> All the icons are gone.  The drives are gone.  The programs are gone.  The files are gone.  And I cannot right-click on the desktop.  I can recover from this by restarting the computer.  I will post a screenshot next time it happens.

Instead of restarting the computer, try restarting the GDM: To restart GDM, switch to Ctrl+Alt+F1, login, give the command

```
sudo /etc/init.d/gdm restart
```

, then when you get the [OK], switch back with Ctrl_Alt_F7.

Or just press Ctrl+Alt+BkSpace.

Did either of these two work-arounds work?

Why does it happen? Thinking about it...

---

### Post by Hollowman on 2008-06-01
This happened to me as well yesterday.  Same thing.  I log in to gdm and no desktop icons or mounted drives. I can still see all the contents in the Desktop folder under Home but I can do drag anything onto the desktop or right click on the desktop.  I tried to restart gdm but it just froze. Any one have any thoughts?  I did update the day before but didn't seem to have any issues.   

HOllowman

---

### Post by Hollowman on 2008-06-03
Whoa, now its back.  I don't know what I did.  8.10 is proving out to not be the most stable.  I will stick it out but I hope the updates will fix the problems. 

Hollowman

---

### Post by strange_cathect on 2008-06-04
I can reproduce this with my machine which has all the updates through yesterday 6/3/08.

It doesn't happen every login, but periodically.  I can always clear it by restarting the GDM, but it is annoying.

---

### Post by lukemack on 2008-06-07
I'm having the same problem but restarting GDM does not work. I have also rebooted, edited the usual nautilus settings etc. I have no desktop icons, no right-click and the Deleted items gnome applet is not working. Ubuntu version is 8.04 (Hardy)

---

### Post by RealMabu on 2008-06-24
Same for me too.
That was after an update that required a reboot.
I believe (but am not sure) that it was right after the release of 2.6.24-19-generic kernel.
So, symptoms:
-/home/myname/Desktop folder still exists and is in good health
-menu bar is fine too
-nautilus displays only the background and nothing can be done there (no new folder, no drag&drop)
-rebooting won't work for me
-under gconf-editor->apps->nautilus->preferences the "show desktop" checkbox IS checked. Tried to run gconf-editor as root also, same result: checked.

Oh, BTW, the OS is working fine, all apps run seamlessly and everything seems to be ok... just NO DESKTOP.:confused:

Any help?

---

### Post by jualin on 2008-06-24
I had a similar problem and apparently the solution was disabling sounds on Pidgin. I think that the bug is caused by PulseAudio. Every time I would run Firefox and Pidgin after a while I would lose my icons and my sounds, and CTRL-ALT-BACKSPACE did not solve the problem, only Hard Rebooting solved the problem.

---

### Post by RealMabu on 2008-06-24
Thanks jualin but this does not fit my case: I don't have Pidgin running at all.
Also, I tried rebooting but it didn't work either.

](*,)

---

### Post by jualin on 2008-06-24
I am sorry that solution did not help you. Maybe someone else has another suggestion.

---

### Post by stikiflem on 2008-06-26
> **prshah said:**
> Instead of restarting the computer, try restarting the GDM: To restart GDM, switch to Ctrl+Alt+F1, login, give the command

```
sudo /etc/init.d/gdm restart
```

, then when you get the [OK], switch back with Ctrl_Alt_F7.

Or just press Ctrl+Alt+BkSpace.

Did either of these two work-arounds work?

Why does it happen? Thinking about it...


hey, this solution worked for me. thanks man. this problem propped out when i put on my flashdrive , reboot while ubuntu was STILL trying to disconnect it. 

thanks again.

---

### Post by ashleycameron on 2008-06-26
I hope then there is the problem with your file system, You change it to NTFS...

---

### Post by wild_oscar on 2008-06-28
I have the exact same problem.

It happens EVERY TIME I do a fresh login (ie, boot my computer up and login). If I logout and login again (or restart X by ctl+alt+backspace) I get my desktop icons and desktop wallpaper (and desktop is clickable).

I have a Gigabytte GA-P35C motherboard and Nvidia 8600 GTS video card, by the way.


It seems that this is an issue that only affects kernel 2.6.24-19-generic. Running Ubuntu on 2.6.24-18-generic does NOT produce the issue!!

Anyone knows how to solve this annoying problem?

---

### Post by RealMabu on 2008-06-30
> **stikiflem said:**
> hey, this solution worked for me. thanks man. this problem propped out when i put on my flashdrive , reboot while ubuntu was STILL trying to disconnect it. 

thanks again.

This solution works for me as well.
Sooner or later some guru will explain me why rebooting doesn't work, while restarting gdm alone works!

Very very annoying bug...

---

### Post by wild_oscar on 2008-07-07
> **RealMabu said:**
> This solution works for me as well.
Sooner or later some guru will explain me why rebooting doesn't work, while restarting gdm alone works!

Very very annoying bug...


I fail to understand how restarting GDM is a solution. I believe it's rather a "band-aid" to cover up the problem, which is not fixed.

Any help in searching for the actual problem is welcome!

---

### Post by RealMabu on 2008-07-07
> **wild_oscar said:**
> I fail to understand how restarting GDM is a solution. I believe it's rather a "band aid" to cover up the problem, which is not fixed.
Yes, I definitely agree.
Restarting GDM *looks like* a solution if you (like me) have a big uptime. My PC never sleeps. Hence, restarting GDM -say- once a week is bearable, at least.

I hope future updates & upgrades will fix this annoyance.

---

### Post by wild_oscar on 2008-07-08
> **RealMabu said:**
> Yes, I definitely agree.
Restarting GDM *looks like* a solution if you (like me) have a big uptime. My PC never sleeps. Hence, restarting GDM -say- once a week is bearable, at least.

I hope future updates & upgrades will fix this annoyance.

Someone suggested me to:

 gconf-editor /apps/nautilus/desktop/volumes_visible

and untick the "volumes_visible" option. I have done it (volumes are no longer visible in the desktop) and it might be working. I have restarted twice and the issue hasn't been created again yet.

It would be nice to see if this is reproducible. Can any of the people with the problem test this?

---

### Post by nights0223 on 2008-07-10
> **wild_oscar said:**
> Someone suggested me to:

 gconf-editor /apps/nautilus/desktop/volumes_visible

and untick the "volumes_visible" option. I have done it (volumes are no longer visible in the desktop) and it might be working. I have restarted twice and the issue hasn't been created again yet.

It would be nice to see if this is reproducible. Can any of the people with the problem test this?

I was having the same problem, so I tried this solution, and it worked!  I don't want the drives visible anyway, so it worked out great.  Thanks.

---

### Post by kingfrollo on 2008-08-17
For those of you using Ubuntu Tweak:
Unchecking *show desktop symbols* in the *Desktop/Desktop Symbols* section will also lead to this issue. Just check it again and it should be solved.

---

### Post by bjoersa on 2008-09-09
> **wild_oscar said:**
> Someone suggested me to:

 gconf-editor /apps/nautilus/desktop/volumes_visible

and untick the "volumes_visible" option. I have done it (volumes are no longer visible in the desktop) and it might be working. I have restarted twice and the issue hasn't been created again yet.

It would be nice to see if this is reproducible. Can any of the people with the problem test this?

hmm. this bug seem to happen when i got a SD card with FAT32 in the slot reader. Remove the card and restart GDM makes icons appear again. Strange must be related to mounting of the filesystem. Anyone else with SD card who can confirm?

---

### Post by simpsonsfan74 on 2008-09-17
I second the above post.  I just started seeing this issue when I started using my new 8GB SDHC card.  I'm also part of the group that sees the error described here for the SDHC card: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247819](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247819)

The no desktop issue for me is temporarily fixed by rebooting gdm, but it comes back upon full boot if my SDHC card is plugged in.

---

### Post by Lucre on 2008-10-16
I've tried everything here and gotten nowhere.  I've tried restarting GDM; I've tried removing my SD card, then restarting GDM; I've tried switching stuff on and off in gconf-editior; I've tried disabling sounds in pidgin; I checked to see that my kernel version was not 2.6.24-19-generic (it's 2.6.24-21-generic); I'm not using Ubunt Tweak.

One other thing - when I use "gksu nautilus", icons show up, but they are in the default position, and the wallpaper has reverted to the default orange swirly heron, so I'm guessing that I'm seeing the root desktop for some reason.

I created a new user and can log in that way to a functional desktop, so if I could migrate my prefs to that user, that might be a workaround for me.

---

### Post by wild_oscar on 2008-10-17
For those with this issue, I suggest following the launchpad bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244244]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244244").

The Ubuntu team asks users to test the bug in the new kernel. I haven't got the time to test it yet, so I just disabled the icons.

---

### Post by njpatel on 2008-10-17
When the background shows and you can right-click or see any folders, it normally means that Nautilus _isn't_ painting the desktop. A quick way to check is to use gconf-editor to navigate to /apps/nautilus/preferences and make sure "show_desktop" check-box is active in the right pane.

In addition to that, use the options in /apps/nautilus/desktop to toggle the visibility of certain things on the desktop (mounted volumes/home icon/trash icon/network icon).

Hope that helps!

---

### Post by Fingel on 2008-10-17
Just kill and restart Nautilus. That should refresh your desktop.

---

### Post by sandwormblues on 2008-11-03
gconf-editor /apps/nautilus/desktop/volumes_visible and unticking Volumes Visible did the trick.

This is a great workaround that solved the problem almost instantly.  I didn't even need to reboot or restart X.  Thanks!

Apparently this problem is related to displaying the volumes.  Is anybody else who has this problem using LVM?  Fuse?

---

### Post by linux_tech on 2008-11-03
To refresh desktop icons you can use-
```
killall gnome-panel
```

Assuming you can view them via ~/Desktop folder in Nautilus but they just  are not appearing on the desktop.

---

### Post by bakshi.hrishikesh on 2009-08-05
> **linux_tech said:**
> To refresh desktop icons you can use-
```
killall gnome-panel
```

Assuming you can view them via ~/Desktop folder in Nautilus but they just  are not appearing on the desktop.

Doesn't Work :(

---

### Post by hxm on 2009-10-20
I have the same problem. It starts when i try to open nautilus. The icons simple disappear.

The solution with gdm restart does not work on me. I use gdm ver. 2.10 so i will try to upgrade that. Nautilus is ver 2.26

---

### Post by azumi123 on 2009-10-21
If this is the same problem I had last night (every Icon vanished off the 
desktop when I was just browsing the hard drive) then it still exists 
in the 9.10 version distributed by LinuxUser magazine. (and therefore a long term issue?) 

Icons I lost included a hard drive & standard terminal

What I also discovered was that every permission on the system - both the 
user and root accounts - had been set back to dissabled. (ie. no permissions to do anything - which "might" be a cause rather than symptom of icon loss I'm guessing?)

Before taking too drastic an action it may be worth others looking for and correcting that if it happens to you.

Az.

---

### Post by KeLa on 2009-10-21
I like to add twist to this.
How can i get rid of all icons of desktop after resume from sleep or hibernation (mainly mounted network shares)??
This because after resume when  trying to go to share i get error message and can't get there.

---

### Post by Akuma_s on 2009-11-04
Maybe your issue is the same discussed here: [http://ubuntuforums.org/showthread.php?p=8240692](http://ubuntuforums.org/showthread.php?p=8240692)

Good luck.

---

### Post by heltonbiker on 2009-12-16
I am having the same problem on the desktop right after startup (no icons, no right click), but things return to normal after I open any program, usually Nautilus or Firefox; when I click the "show desktop" icon (which I have at the quicklaunch menu), the desktop is fine.
Hope it will be identified and fixed by updates.

---

### Post by deadBee on 2010-02-09
I am having that problem too, but it is not a problem actually

I dont remember how I ve done it but there is a way to disable desktop icons, which I ve done to make a screensaver or animated background. Now Im trying to turn them back on.

ps.Its not gconf-editor /apps/nautilus/desktop/volumes_visible, ive checked it. Something on the terminal maybe.

---

### Post by cypherdtraitor on 2010-02-09
I've been running into this problem as well. As previously mentioned, using the f2 terminal and executing "sudo /etc/init.d/gdm restart" has worked for me. Keep in mind I do this as administrator.

I would recommend against trying this in the terminal application, which as a general rule can't seem to override the GUI in any way.

---

### Post by variona on 2010-02-10
In my case the problem occurs after a session crahes. I have a little script which removes files which are session relevant

(don't forget to backup the files/directories and check that recursive removal (rm -r) does end in the directory you want to remove)
You will have to replace USER with your login name :
```

#/bin/bash
rm -r /tmp/orbit-USER 
#I need to do that when the session does not start at all - then I have to start the script from a text console, or sudo USER from another users desktop
rm -r /tmp/gconfd-USER
rm /home/USER/.gnome2/session
#end of script

```

HTH
Variona


Quote from [http://library.gnome.org/misc/release-notes/2.0/](http://library.gnome.org/misc/release-notes/2.0/)
There have been cases of the initial login to GNOME 2 not going quite smoothly and a lot of errors about CORBA connections not being completed popping up in error boxes (and nothing else starting). This can be probably fixed by stopping the session (returning to the gdm screen or to the command prompt) and then (in a terminal) removing the /tmp/orbit-user directory (and all of its contents), where user is replaced with the appropriate user's login name.

---

### Post by Wardje on 2010-02-10
When this occurs to me, it tends to happen while I am doing something already. Not at startup.

In this case it just ends up to be Nautilus not running anymore. So basically it crashes because of whatever I was doing. To check if it is running still or not, open a terminal and type
```
ps aux | grep nautilus
```
and see what it returns

Note: if it says
```
nautilus --no-desktop --browser /some/path
``` then I think it's pretty obvious what's happening :D

Either way, close all nautilus windows you might still have running, press ALT+F2 and type in ```
nautilus
```

Fixes it for me

---

### Post by Awareness on 2010-03-09
> **Fingel said:**
> Just kill and restart Nautilus. That should refresh your desktop.

This just worked fine... thanks :D

---

### Post by dowell_p on 2010-03-09
> **Wardje said:**
> When this occurs to me, it tends to happen while I am doing something already. Not at startup.

In this case it just ends up to be Nautilus not running anymore. So basically it crashes because of whatever I was doing. To check if it is running still or not, open a terminal and type
```
ps aux | grep nautilus
```
and see what it returns

Note: if it says
```
nautilus --no-desktop --browser /some/path
``` then I think it's pretty obvious what's happening :D

Either way, close all nautilus windows you might still have running, press ALT+F2 and type in ```
nautilus
```

Fixes it for me

This works for me. I have the problem when I click on the network icon in my places menu

---

### Post by bitsmart on 2010-03-20
OK I had the same problem. When someone mentioned gconf-editor /apps/nautilus/desktop/volumes_visible I started poking around the nautilus settings and found this:

Under the gconf tree for Nautilus>Preferences>Show_Desktop

Icons are back! Yay!

---

### Post by jdorenbush on 2010-05-05
Here is a bug that is possibly related to this: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/329146](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/329146)

I'm having this problem too and am trying to narrow down what the problem is.

---

### Post by Jaded Phoenix on 2011-01-26
Guys, I've just solved the very same problem:
Everything is OK, except - the desktop is empty and unclickable.

First, I figured out that pressing Alt+F2, typing "nautilus" and pressing "OK" brings the desktop back.

Then, I remembered my recent changes to the environment:
I had an entry in the "Startup applications" menu (System/Parameters/Startup applications). This entry started nautilus with some command-line parameters. Recently I wrote a script to do the needed settings, and replaced "nautilus blah-blah-blah" with "my-super-script".

Now I opened Terminal and entered these commands:
```

cd ~/.config/autostart/
ls

```
and - BUMP! I got this:
```
nautilus.desktop update-notifier.desktop
```

This was it: I still had a custom entry called nautilus.desktop, but it didn't launch Nautilus any more! So I just entered
```

mv nautilus.desktop my-script.desktop

```
and voila, after reboot I'm happy to see my precious desktop.


Sorry for long post, hope it helps someone else think in the right direction

---

