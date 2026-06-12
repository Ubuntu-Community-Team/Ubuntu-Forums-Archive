---
title: "How to disable screensaver"
date: 2013-05-03
forum: Desktop Environments
---

### Post by jeffbarish on 2013-05-03
I am running lubuntu 12.04.  I would like to completely disable the screensaver.  Here's what I've done so far:

1. Under Preferences | Power Manager | On AC | Monitor: set both sliders for Monitor to 0 (Never).

2. Under Preferences | Screensaver Preferences: set Mode to Disable Screen Saver.

3. Under System Tools | dconf-Editor, org | gnome | desktop | applications | screensaver: idle-activation-enabled and lock-enabled unticked.

4. apt-get purge xscreensaver xscreensaver-data

The display still blanks after 5-10 minutes.  Any idea what I missed?

---

### Post by Dennis N on 2013-05-04
Had the same problem. If I remember correctly, this fixed it:

[B]Preferences > Power Manager > General : Uncheck 'Monitor Power Management Control'
[/B]
which inhibits the power manager from putting the monitor into sleep mode.

With this, monitor stays on always,  and any screensaver (if enabled) would work after the set amount of time for inactivity.

---

### Post by jeffbarish on 2013-05-04
I tried that setting too.  Makes no difference.  I wasn't sure what its purpose was supposed to be, so I did not report that test previously.  I even tried rebooting after unchecking the box.

I tried setting the slider for "Put display to sleep when computer is inactive" to 1 minute.  With the box "Monitor power management control" checked, the display went dark at 1 minute.  With the box unchecked, the monitor did not go dark at 1 minute.  I conclude that the Xfce Power Manager is doing what it is expected to do.  However, no matter how I set anything on this panel, the display goes dark at 10 minutes.  It seems as if something else is blanking the screen.

BTW, I have two platforms suffering from this problem.  This problem is new.  For certain I was previously able to turn off the screensaver using only steps 1 and 2 on my list.

---

### Post by Dennis N on 2013-05-04
I did a test for my own information, and also to recheck that I didn't give you bad information.

Two Computers, Laptop running Lubuntu 13.04, Desktop running Lubuntu 12.10
[obvious difference here, in that you have Lubuntu 12.04 - might be a factor.]

> Laptop Setup of Power Manager:

General
Monitor Power Management control : Unchecked for this test (originally it was checked, and the power manager was known to be working and to shut down the display as set in the Monitor tab)

OnAC
Actions tab
when laptop lid is closed: lock screen
Put the computer to sleep when inactive for: never
Monitor tab
Monitor options to put display to sleep or switch off display are set for 20 min. and 45 min.
Brightness
Reduce screen brightness when inactive for: never

Screen Saver Options
Screen Saver Disabled

Laptop was run on ac power for one hour untouched. Screen remained full-on throughout that time. The monitor tab settings were ignored, since power management option was unchecked in General Tab. That is how I thought it was supposed to work, and that was confirmed.

> Desktop Setup

General
Monitor Power Management control : Unchecked

OnAC
Actions: 
Put to sleep when inactive: Never
Monitor
Both sliders set to never.

Screensaver Options:
Selected screensaver set for one hour.

Desktop also ran for an hour. Monitor remained full-on until my screensaver kicked in at 1 hour as expected. Stopped the test at that point. Everything as expected.

The obvious difference is that you are running Lubuntu 12.04, and I don't have that version anymore. The packages for xfce4-power-manager are not the same version. You can investigate that, and look at the changelogs or bug reports.

Also, I never used dconf to change any settings on my systems.

---

### Post by Dennis N on 2013-05-04
Forgot to add this in:

Documentation for xfce4-power-manager:

[http://docs.xfce.org/xfce/xfce4-power-manager/getting-started](http://docs.xfce.org/xfce/xfce4-power-manager/getting-started)

Unfortunately, an older version is described there - page last updated Mar 2012. Still may have something you can use.

Good Luck.

---

### Post by Rex Bouwense on 2013-05-04
OK, something is definitely screwy.  I have Lubuntu 12.04 and Lubuntu 12.10 on my ASUS netbook.  I had to reboot to get back into 12.04 and I  used the described procedures to disable the screen saver.  I didn't wait an hour but for 30 minutes the screen remained the same.  Previously I had set the screen saver to come on in 10 minutes.

---

### Post by jeffbarish on 2013-05-04
Thanks, guys.  It's especially interesting to know that 12.04 works for someone else.  I gather that you don't run 12.04 often.  Did you try doing all updates?  I'm pretty sure that the problem occurred on my system as a result of some update because, as I said before, I didn't have this problem some time ago.

I tried uninstalling xfce4-power-manager.  I don't even have the configuration panel we have been discussing anymore.  I previously uninstalled xscreensaver.  The screen still blanks at 10 minutes.

I discovered that the changes I made with dconf-editor had reverted to their default values.  I made the changes again.  The screen still blanks at 10 minutes.  Obviously something else is causing the screen to blank.  Could it be the monitor itself?  I don't see any options to that effect in the menu.  Could it be UEFI?  Again, I don't see anything relevant there.  I looked through the output of ps aux.  I don't see anything there that looks relevant, but as you know there are a lot of things running with obscure names.

It would be very interesting to know whether someone running 12.04 *with all updates* sees this problem.  You don't have to wait more than 10 minutes.

---

### Post by Rex Bouwense on 2013-05-04
Perhaps I was holding my mouth just right.  My 12.04 is up to date.  I ran the software updater just before I tried the procedure.  Somewhere in the closet I have a very old Dell Inspiron 1000 with Lubuntu 12.04 installed.  I haven't played with it for a month or so.  I'll get it out and see if I can disable the screensaver.  It needs something new on it anyway.

---

### Post by jeffbarish on 2013-05-04
I found the problem.  It's X11.  It has something called DPMS.  By default, it blanks the screen at 10 minutes (just as I was seeing).  To fix the problem, I created a file called 10-disable-dpms.conf in /etc/X11/xorg.conf.d (which I had to create) containing:

Section "ServerFlags"
    Option "BlankTime"  "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection


I'm pretty sure I saw an X upgrade go by some time ago, so I bet that's when this problem started.

Thanks anyway for the suggestions.

---

### Post by Buntu Bunny on 2013-05-05
Can you guys install Caffeine? I don't know anything about Lubuntu software, but it's in the Ubuntu Software Centre and is what I use. 

Caveat: I don't know if it's a permanent disable, might just be per session.

---

### Post by jeffbarish on 2013-05-05
I considered caffeine, but it is not in the repository for Lubuntu 12.04.  In any case, I prefer to avoid adding another dependency -- especially in a case where the problem was caused by too many dependencies with overlapping functionality.

I wanted to add one comment to my posting with the solution to the problem.  I am having trouble understanding why X11 provides both DPMS and xscreensaver, considering that the functionality of the first appears to be subsumed by the second.  Moreover, xfce4-power-manager triplicates some of the functionality.  Having three modules performing the same functions seems like a bad design.  Also, if my belief is correct that a recent upgrade to X11 activated the DPMS functionality, then a lot of users are going to be surprised as I was when their configuration of xfce4-power-manager and xsreensaver mysteriously stops working.  This seems like a particularly poor upgrade policy for an LTS release.

---

### Post by Rex Bouwense on 2013-05-05
Got the old Dell out of the closet and after updating the kernel to 3.2.0.41, it works like a charm.  I just thought of something that perhaps you were not doing.  Under Memu->Preferences->Power Manager there is a box for disabling DPMS under the General Tab.  Did you have that checked before you found your solution?

By the way Lubuntu 12.04 is not a LTS release.  As of this moment there is no LTS release for Lubuntu.  They do not have the manpower to support the versions.

---

### Post by espen.k.nilsen on 2013-11-13
> **jeffbarish said:**
> I found the problem.  It's X11.  It has something called DPMS.  By default, it blanks the screen at 10 minutes (just as I was seeing).  To fix the problem, I created a file called 10-disable-dpms.conf in /etc/X11/xorg.conf.d (which I had to create) containing:

Section "ServerFlags"
    Option "BlankTime"  "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection


I'm pretty sure I saw an X upgrade go by some time ago, so I bet that's when this problem started.

Thanks anyway for the suggestions.


 This works in lubuntu 13.10 also.

Example

```

cd /etc/X11
sudo mkdir xorg.conf.d
cd xorg.conf.d
sudo touch 10-disable-dpms.conf
sudo nano 10-disable-dpms.conf 
#Add code from comment (copy/paste)

```

---

### Post by buzzingrobot on 2013-11-13
In 13.10, the "Brightness and Lock" settings panel -- distinct from the screensaver -- inlcudes settings to lock and turn off the screen after a specified period. Or, not.

---

### Post by vasa1 on 2013-11-13
> **buzzingrobot said:**
> In 13.10, the "Brightness and Lock" settings panel -- distinct from the screensaver -- inlcudes settings to lock and turn off the screen after a specified period. Or, not.
The posters have **L**ubuntu in mind. Is your answer relating to Ubuntu? I'm not seeing a "Brightness and Lock" settings panel in Lubuntu 13.10.

---

### Post by buzzingrobot on 2013-11-13
> **vasa1 said:**
> The posters have **L**ubuntu in mind. Is your answer relating to Ubuntu? I'm not seeing a "Brightness and Lock" settings panel in Lubuntu 13.10.

Ah, yep, Ubuntu.  Sorry.   Odd if it's been removed, tho.

---

### Post by vasa1 on 2013-11-14
> **buzzingrobot said:**
> Ah, yep, Ubuntu.  Sorry.   Odd if it's been removed, tho.
:)

No idea but a Xubuntu user has been reporting something similar (I think): [https://lists.ubuntu.com/archives/xubuntu-users/2013-November/006163.html](https://lists.ubuntu.com/archives/xubuntu-users/2013-November/006163.html)

I took another tack and I'm using a small script to run every 8 min; it uses xdotool to send a keypress of the shift key every 8 min when the CPU usage exceeds a set value (like when I'm watching a video).

BTW, I don't see the screen getting locked at any time. If I leave my laptop unattended (with minimal CPU usage) the screen just goes blank and never locks. I'm a single user and don't have to worry about others touching my lappie. I don't have any screensaver installed and xscreensaver isn't part of Lubuntu 13.10, AFAIK.

---

### Post by acornblue on 2014-04-30
this is for pple who find this googling for answers.
[ solution ] from cmdline &#12299;xset s off && xset -dpms
that should disable screensaver & powersaver.
u can also change timed to 1hr like so
&#12299;xset s 3600 && xset dpms 3600

finally to re-enable
&#12299;xset s on && xset +dpms

---

### Post by Peppe_L-G on 2014-11-16
> **jeffbarish said:**
> To fix the problem, I created a file called 10-disable-dpms.conf in /etc/X11/xorg.conf.d (which I had to create) containing:

Section "ServerFlags"
    Option "BlankTime"  "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection

This worked for me (Lubuntu 14.04). Thanks!

---

