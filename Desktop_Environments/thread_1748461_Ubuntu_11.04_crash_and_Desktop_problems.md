---
title: "Ubuntu 11.04 crash and Desktop problems"
date: 2011-05-03
forum: Desktop Environments
---

### Post by footloose.raman on 2011-05-03
Hello People,

I upgraded my desktop to 11.04 and am experiencing the following problems.

1. The new desktop tool bar program on the left side of the screen seems to have crashed. It worked for a couple of days and after an abrupt power off(cable got snapped), the system reverted to the old desktop look and feel(10.10). Can some one share some knowledge ?

2. The system hanged while playing gtk-gnash. At least once it printed the following information before everything froze.
Process Involved : gtk-gnash
Bug : Could not handle the kernel request for paging
I could not copy anything 'cos the screen was frozen but I recollect these points from among the stack trace and lots of memory pointers.

3. The system simply crashed once. :) Though again playing youtube only.

Well, it seems to me Natty Narwhal is some what unstable.
Please share your experience or could some one suggest any fixes or possible reasons. I will love to dig into this.

cheers...

---

### Post by opiumpoetry on 2011-05-03
Natty crashes a lot whether you're using Unity or Ubuntu Classic (GNOME). And it doesn't matter what you're doing, it just crashes once or twice a day. Too bad. I expected Ubuntu to get better, not worse.

---

### Post by TJet1.8 on 2011-05-03
Same here...quite unstable.

Anyone know what the Ubuntu Team is doing about this?
Are bug reports being sent?

I am a bit dis-appointed with this release.

As opiumpoetry mentioned, I expected better...:(

---

### Post by pedanticmofo on 2011-05-05
I've also had the system lock up a few times after I upgraded to 11.04.  Usually just when running Firefox and a few PDFs in Document Viewer under the Ubuntu Classic interface.

The Alt+SysRq+REISUB thing works to reboot the system, but nothing else seems to.

---

### Post by gregalynch on 2011-05-05
I'm also using Ubuntu classic and have had 1-2 crashes a day.  It typically just goes back to the login screen and I have to log in again.

---

### Post by danice on 2011-05-06
I have the same problem... ubuntu 11.04 crashes in classic and the new desktop...
It happens every hour or two.
(the new desktop is very nice... I hope this problems could be solved quicky!)

---

### Post by DrDavidHart on 2011-05-07
I installed a 11.04 from scratch, several times, and it crashes right after login or it waits for an hour and ever where in between.  I really like Ubuntu, I hope this is fixed soon.  I have a Toshiba laptop running Windows 7 ultimate and I installed Ubuntu beside it on a separate partition.  I had it on a USB stick for awhile and it did the same thing.  Crash, crash....  When it runs, it is awesome.
Can anyone help?
Thanks,
Dr David

---

### Post by ngronewold on 2011-05-07
It might be a hardware issue. The Unity desktop sucks more out of the CPU, which is why the OS is trying to default to the classic feel. Maybe a memory boost will fix?

I'm also beginning to suspect that, for whatever reason, Ubuntu and Toshiba don't get along.  A lot of the catastrophic problems I read about here involve Toshiba desktops and laptops. Dell users seem to have minimal issues (me included). I went from 10.04 to 11.04 and, aside from a temporary wireless problem, everything is smooth sailing.

---

### Post by foohbah on 2011-05-07
I'm having random desktop crashes on a lenovo t61 - desktop returns to login screen and I lose all my open applications...

Was perfectly stable with 10.10 before the 11.04 upgrade. 

I found the unity desktop to be quirky and (for me) not helpful so swapped back to 'ubuntu classic' (gnome) almost immediately after upgrading.

I wonder whether I need a clean install - which will be annoying..

Might turn off visual effects and see what happens.

Bad enough to downgrade :confused:

---

### Post by jscudder on 2011-05-14
Natty 11.04 Ubuntu Classic randomly crashes and takes me back to login screen also.  Does this on both my Dell Laptop running Ubuntu 11.04 32 bit and Dell Desktop running 11.04 64 bit. 

Both had clean installs.  Crashes occurred while using Firefox and LibreOffice.

---

### Post by woozalia on 2011-05-15
I've been having the same problem described by many users here -- I come back to my computer and find it at the login screen.

I have found one application which reliably triggers this event: gnome-power-manager -- simply running it causes an immediate crash, and the login screen comes up right away. From past experience, this would seem to indicate that XOrg has been restarted.

Here is an excerpt from Xorg.0.log.old:

> Backtrace:
[ 14305.324] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[ 14305.324] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[ 14305.324] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xa4640c]
[ 14305.324] 3: /usr/lib/xorg/modules/drivers/openchrome_drv.so (0x679000+0x26798) [0x69f798]
[ 14305.324] 4: /usr/bin/X (0x8048000+0x140c26) [0x8188c26]
[ 14305.325] 5: /usr/bin/X (0x8048000+0x141682) [0x8189682]
[ 14305.325] 6: /usr/bin/X (miHandleValidateExposures+0x83) [0x81bc133]
[ 14305.325] 7: /usr/bin/X (MapWindow+0x257) [0x809b137]
[ 14305.325] 8: /usr/bin/X (0x8048000+0x22023) [0x806a023]
[ 14305.325] 9: /usr/bin/X (0x8048000+0x28167) [0x8070167]
[ 14305.325] 10: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[ 14305.325] 11: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x500e37]
[ 14305.325] 12: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[ 14305.325] Segmentation fault at address 0x1ec
[ 14305.325]
Caught signal 11 (Segmentation fault). Server aborting
[ 14305.325]
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[ 14305.325] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 14305.325]After removing gpm, my system became much more stable -- it survived an  entire night, only to crash the next night, so apparently the problem is  not isolated to gpm.

It has never rebooted while I was actually *using* it, except when I tried to run gpm.

The problem started when I ran an upgrade from 10.10 to 11.04, which locked up and had to be cleaned up by running dpkg manually. After that, I tried "upgrade from 11.04 to 11.04" on the liveCD, which also had some kind of problem near the end -- and my mouse would no longer work. I ran that upgrade one more time, this time without error, but the mouse did not recover. (It worked fine when booting from the liveCD, just not from the resulting system on the hard drive.)

At that point, I went out and got a fresh hard drive and did a clean install, which is where I am now.

This is a severe problem, especially since this version of Ubuntu does not seem to be saving my desktop configuration properly (normally a minor problem I could live with; not so much when the system randomly reboots), so I hope it can be tracked down and fixed soon.

---

### Post by woozalia on 2011-05-16
Since my previous post, I tried an experiment. I wiped the hard drive again and started with a clean system. I verified that the power manager app did not crash at this point. I then began re-installing all the things I had installed yesterday, and testing the app in between each installation, hoping to catch the particular item whose installation caused the crashing to commence.

It never happened.

I did notice one thing, though. The latest kernel installed on my old hard drive (which I had upgraded to 11.04) is 2.6.38-9. The kernel now installed on my clean system is 2.6.38-8. I ran a full update after reinstalling, and it did not upgrade the kernel.

I can only conclude that the folks in charge of packaging were able to isolate the problem as being a bug in the 2.6.38-9 kernel, and have pulled it out of distribution. My thanks to them if this is so.

My system seems stable now, although the real test will be to run through a week's (or month's) worth of overnight cron jobs and see if it survives.

---

### Post by wildmanne39 on 2011-05-16
Hi, the only time I had a problem with crashing was when I upgraded, I had to do a fresh install, and right after I had to use the 173 nvidia driver for my graphics card not the current one. But it is working great, also you can not enable any effect in compiz when running unity, if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all.:p

---

### Post by woozalia on 2011-05-17
My system survived the night, but then it wanted to do a package update right before I went out. I looked at the packages and didn't see any kernel updates, so I authorized the upgrade to start and then left.

When I came back, it was back to the login prompt. After logging in, I can run the power management app directly, but it crashes if I run it from the screen saver dialogue.

So something still isn't right.

I'm in the process of backing things up again so I can do another fresh install and see where the problem creeps in.

---

### Post by woozalia on 2011-05-17
Ok, here's the latest. It seems to be a conflict with ElectricSheep (the distributed computing screensaver). I can list all the gyrations I went through to pin this down, but the final sequence is this:

Fresh system with all applications reinstalled and all config files restored from my original system works fine -- power manager app runs using either method.

However, once the screen saver dialogue has displayed ElectricSheep once, if you press the "Power Management" button while esheep is running, it crashes.

After logging back in, switch to another screen saver, press the button -- no crash.

I can only imagine this is something fairly hardware-specific, or it would have been caught during development.

Hope that's helpful, and hope it gets fixed soon. I miss esheep. :-(

---

### Post by skatebiker on 2011-05-20
Same here on my HP Pavilion 6710 (2008 model).
10.10 ran flawlessly but 11.04 has a few random crashes a day. After a login it seems that all programs I start at login are loaded.

An excerpt of /var/log/Xorg.0.log.old :


/
Backtrace:
[  4484.429] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[  4484.429] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[  4484.429] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x26840c]
[  4484.429] 3: /usr/bin/X (_CallCallbacks+0x3e) [0x8074e1e]
[  4484.429] 4: /usr/bin/X (WriteToClient+0x267) [0x80a7607]
[  4484.429] 5: /usr/lib/xorg/modules/extensions/libdri2.so (ProcDRI2WaitMSCReply+0x62) [0x361bf2]
[  4484.429] 6: /usr/lib/xorg/modules/extensions/libdri2.so (DRI2WaitMSCComplete+0x75) [0x35ffc5]
[  4484.429] 7: /usr/lib/xorg/modules/drivers/intel_drv.so (0x1c7000+0x226bc) [0x1e96bc]
[  4484.429] 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0x1c7000+0x87d2) [0x1cf7d2]
[  4484.429] 9: /lib/i386-linux-gnu/libdrm.so.2 (drmHandleEvent+0xf5) [0x630665]
[  4484.430] 10: /usr/lib/xorg/modules/drivers/intel_drv.so (0x1c7000+0x7937) [0x1ce937]
[  4484.430] 11: /usr/bin/X (WakeupHandler+0x52) [0x8074602]
[  4484.430] 12: /usr/bin/X (WaitForSomething+0x1ba) [0x80a1f3a]
[  4484.430] 13: /usr/bin/X (0x8048000+0x27f1e) [0x806ff1e]
[  4484.430] 14: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[  4484.430] 15: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xd6be37]
[  4484.430] 16: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[  4484.430] Segmentation fault at address 0xa7fbc008
[  4484.430] 
Caught signal 11 (Segmentation fault). Server aborting
[  4484.430] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  4484.430] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  4484.430] 
[  4484.440] (II) Power Button: Close
[  4484.440] (II) UnloadModule: "evdev"
[  4484.440] (II) Unloading evdev
[  4484.444] (II) Video Bus: Close
[  4484.444] (II) UnloadModule: "evdev"
[  4484.444] (II) Unloading evdev
[  4484.448] (II) Sleep Button: Close
[  4484.448] (II) UnloadModule: "evdev"
[  4484.448] (II) Unloading evdev
[  4484.452] (II) Microsoft Microsoft® Digital Media Pro Keyboard: Close
[  4484.452] (II) UnloadModule: "evdev"
[  4484.452] (II) Unloading evdev
[  4484.457] (II) Microsoft Microsoft® Digital Media Pro Keyboard: Close
[  4484.458] (II) UnloadModule: "evdev"
[  4484.458] (II) Unloading evdev
[  4484.461] (II) Microsoft  Microsoft Basic Optical Mouse : Close
[  4484.461] (II) UnloadModule: "evdev"
[  4484.461] (II) Unloading evdev
[  4484.464] (II) AT Translated Set 2 keyboard: Close
[  4484.464] (II) UnloadModule: "evdev"
[  4484.464] (II) Unloading evdev
[  4484.475] (II) UnloadModule: "synaptics"
[  4484.475] (II) Unloading synaptics
[  4484.476] (II) HP WMI hotkeys: Close
[  4484.476] (II) UnloadModule: "evdev"
[  4484.476] (II) Unloading evdev
[  4484.477] (II) AIGLX: Suspending AIGLX clients for VT switch
[  4484.552]  ddxSigGiveUp: Closing log

---

### Post by Holek on 2011-05-23
[img]http://dl.dropbox.com/u/23165202/ubuntu.png[/img]

---

### Post by kazelux on 2011-05-23
> **opiumpoetry said:**
> Natty crashes a lot whether you're using Unity or Ubuntu Classic (GNOME). And it doesn't matter what you're doing, it just crashes once or twice a day. Too bad. I expected Ubuntu to get better, not worse.


Same behaviour, with a Dell Latitude E4300. From time to time the graphical interface simply crashes and the login prompt is shown again.

Would be a minor nuisance if all the programs being run were not aborted as well.

---

### Post by LoganDimond on 2011-05-24
I just got a laptop last week, an Asus k52f bin6, and decided to try a Linux distro for the first time. I installed Ubuntu Studio 11.04. I love many things about it, but crashing 1-2 times/day isn't one of them. I'm missing Windows (:confused:), but I'm also really falling in love with open source in general and can imagine how great this OS would be if it was more stable. 

I've not noticed anything triggering it so far. Either it just freezes, the mouse will not work on anything related to the top (and only) panel, or it just spontaneously goes back to the user sign in screen. Also, highlighting (or doing anything with) the mouse is sketchy.

I'm not sure if this is related to what other people are describing in the thread of if I'm just messing something up; what's my best course of action? Switching to 10.10?

---

### Post by Rajivas on 2011-05-25
11.04 crashes on my Compaq presario cq45 laptop (4GB Ram, Turion X2)  atleast 3 times a day. The issue is present both in unity and classic.  after crash it again goes back to login page. I expected better from Ubuntu.

---

### Post by David of Broadway on 2011-05-29
Same problem on my Lenovo IdeaPad Y530.  I've only been using GNOME since upgrading ("Classic") - never had any interest in trying Unity, and it doesn't look like it'll help me here.

---

### Post by olamina on 2011-06-06
This instability sucks,  but I'm relieved to see other people are having the same problem. At this point, I'm used to having to do a daily reboot. I won't degrade however since the previous version made my wireless next to impossible to use. 

Looking forward to this getting fixed, and I'll do what I can to file bug reports!

---

### Post by Thirtysixway on 2011-06-06
Any updates on this bug? I've yet to find a solution for it.

---

### Post by electricgypsy on 2011-06-10
Am having problems with 11.04 crashing to logon too AND i'm using a Toshiba laptop (an Equium M50 - 164)...so what '**ngronewold**' says about _Ubuntu & Toshiba compatability probs_ (?) is a cause for concern! :( Wish i hadn't gone for the upgrade now...nice as this 'funky' new desktop looks.

---

### Post by liztrd on 2011-06-11
Linux Mint Debian Edition(LMDE) is a good replacement of Ubuntu 11.04
LMDE is a rolling edition,which mean it upgrade without reinstall system and it is more stable than ubuntu 11.04&#65281;&#65281;
And it's fast,very fast

---

### Post by kervin on 2011-06-11
It is crashing a lot. What should I do in those situations? Should I power off, cause I do not seem to be able to do anything. mouse does not move and keyboard does not respond... :( where is my 10.10...

---

### Post by vinjvinj on 2011-06-29
I have a T510 and upgraded from 10.04. to 11.04. It crashes 2-5 times daily as well. I've downgraded the power management as some have suggested and turn off the wirless before suspend. That has helped a little bit but not much. 

Hopefully they can have it fixed.

---

### Post by Frogs Hair on 2011-06-29
Ubuntu has never crashed in four different releases . I don't know what I am doing differently , I have similar hardware to many people . :confused:

---

### Post by ethantime on 2011-06-29
Same here.  Just put 11.04 on my mom's desktop and now it's crashing 4-6 times/day.  I'm not nearby, so I can't easily revert to an earlier release.

any news on updates or fixes?

---

### Post by Russ.pinkslippa on 2011-07-26
hey guys,  I use classic desktop for my 11.04, when it crashes i do:  crtl + alt + f1 (1-6) for terminal then  sudo service gdm restart  and that does the trick. You loose all your current windows but it's better than restarting.  Hope that helps somewhat :)  Russ

---

### Post by scorp123 on 2011-07-26
> **thrallgg said:**
> I have the same problem... ubuntu 11.04 crashes in classic and the new desktop :( I told you so (... in another thread ...)

Since I downgraded my MacBook Pro to Ubuntu 10.10 again everything is running like a dream.

I am now busy downgrading my main desktop PC. Kubuntu 11.04 froze that system several times today (something which never happened with Ubuntu 10.10 + Gnome 2!) and I've had enough, I am downgrading it back to Ubuntu 10.10 again.

So ... no Ubuntu or Kubuntu 11.04 for me. It's just too unstable and it crashes all the time. Or it freezes the system without giving a clue how and why. Thank you but no thank you. I am back to Ubuntu 10.10 for now.

---

### Post by mantorpcity on 2011-08-22
My 11.04 was working OK for weeks, but the last 3 - 4 days it started crashing several times per day. I guess it's some update, but it's driving me nuts. Only thing that works is press and hold the power button for 5+ seconds. Interestingly, it started on my Pavilion the same day HP announced they're quitting the PC business, coincidence or conspiracy?

---

### Post by TweFoju on 2011-09-30
Yep, this happen to me also

just used 11.04 for a couple of days

even when i am just clicking around sometimes the Desktop hangs 

i hate it when i have to force shutdown my laptop

it crashes randomly, sometimes doing nothing can even crash

hopefully 11.10 is soon!

and im using Kernel 3.0.0-0300

i thought it was the Kernel, but it's just the OS that is unstable

---

### Post by system11 on 2011-10-19
Has anyone found a solution for this?  Default clean install of 11.04 and the desktop just vanishes shortly after login sometimes.

---

