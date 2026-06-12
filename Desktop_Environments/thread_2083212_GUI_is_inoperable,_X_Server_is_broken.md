---
title: "GUI is inoperable, X Server is broken"
date: 2012-11-11
forum: Desktop Environments
---

### Post by Destructo47 on 2012-11-11
Lately, X has been having random hangups that have caused me to either reboot or log out with Alt+SysRq+K (other commands did nothing after the freeze). Some of them have been three seconds after login, and others have taken longer to happen. I tried removing X with **sudo apt-get purge lightdm** and then reinstalling to see if that fixed anything. Now I don't have a GUI to work with. I rebooted, and it gave me the "Could not determine your hardware" screen (the one with the option of booting in low graphics mode). I tried booting in low graphics mode, but all I get is a maintenance shell as root. **sudo service lightdm start** logs me into a regular console, but still no GUI.

At this point, typing **exit** brings me back to the maintenance shell, but no GUI of any sort. typing **exit** here just reboots the computer. Using a Backtrack LiveDVD, I managed to create a xorg.conf that *should* work, but instead I get a completely blank screen at boot. I noticed during the uninstall of lightdm that there was a brief message saying there were no more users left of a group. Could that be the issue, or is there another problem?

---

### Post by Destructo47 on 2012-11-13
Could someone explain to me why threads I start are constantly ignored? I don't mean to whine, but it really aggravates me. Is there something I've done or am doing wrong here?:confused:

---

### Post by mardybear on 2012-11-13
Hi Destructo47.

It can take up to a day for people to respond - volunteers only i believe.

Please clarify so people can better assist:

Which flavour of Ubuntu are you using, including desktop environment?

When you cold boot your computer, do you manage to get a graphic login screen and then a black screen when you attempt to login?

Edit: Does any of this help: [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

mardybear

---

### Post by Destructo47 on 2012-11-14
Not trying to be rude, but that took two days, and I probably wouldn't have gotten a reply if I hadn't complained about it. I understand the website is made of volunteers, but I have multiple threads open with no answers to them (some have been that way for years).

Let's just say my problem applies to the last bullet under 'What to do if things go wrong' on the page of the link you gave me: no graphical display after the BIOS whatsoever. After a point, my monitor gives me the 'No Signal' message, and goes blank.

I'm using vanilla Ubuntu 12.04 under Gnome shell. When I could boot, it just went to the last environment I logged into (Recovery Shell, Gnome Classic without FX, etc.). Unfortuantely, after trying to fix it myself (as I mentioned above), I don't get a display after the BIOS and dmi pool check. Interestingly, if I wait long enough after turning the computer on, I get the purple shutdown screen if I hold down the power button.

Right now, I'm using a BackTrack 5 LiveDVD to run the box. Here is the log of /var/log/lightdm/lightdm.log (since the forum doesn't like .log files):

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1000
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for automatic login as user nick
[+0.00s] DEBUG: Starting local X display
[+0.06s] DEBUG: X server :0 will replace Plymouth
[+0.09s] DEBUG: Using VT 7
[+0.09s] DEBUG: Activating VT 7
[+0.09s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.09s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.10s] DEBUG: Launching X Server
[+0.10s] DEBUG: Launching process 1055: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.10s] DEBUG: Waiting for ready signal from X server :0
[+0.10s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.10s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.18s] DEBUG: Process 1055 exited with return value 1
[+0.18s] DEBUG: X server stopped
[+0.18s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.18s] DEBUG: Releasing VT 7
[+0.18s] DEBUG: Stopping Plymouth, X server failed to start
[+0.24s] DEBUG: Display server stopped
[+0.24s] DEBUG: Stopping display
[+0.24s] DEBUG: Display stopped
[+0.24s] DEBUG: Stopping X local seat, failed to start a display
[+0.24s] DEBUG: Stopping seat
[+0.24s] DEBUG: Seat stopped
[+0.24s] DEBUG: Required seat has stopped
[+0.24s] DEBUG: Stopping display manager
[+0.24s] DEBUG: Display manager stopped
[+0.24s] DEBUG: Stopping daemon
[+0.24s] DEBUG: Exiting with return value 1
```Specifically, these two lines:

```
[+0.18s] DEBUG: Process 1055 exited with return value 1
[+0.18s] DEBUG: X server stopped
```I'm not entirely sure what program that process 1055 refers to, but it does look like that's the problem. Of course, how do I fix it? Using SSH won't work with my setup, but GRUB recovery mode might work. However, I'm not sure what key to press to initiate recovery mode. Suggestions from some sites have done nothing.

Is that clear enough, or do I need to elaborate some more (not being sarcastic)?

By the way, thank you for responding and attempting to help.

EDIT: A Google search tells me that process 1055 is tty6...the default GUI console. So I'm back to square one, because I don't know why it returns with the signal 1 instead of 0.

---

### Post by grahammechanical on 2012-11-14
You are not only angry but unclear about some things. Such as the difference between the Xserver and LightDM. You say this:

> I tried removing X with sudo apt-get purge lightdm

Without X you wont even get a command-line version of Linux. Purging LightDM removed the log in screen. As you are using Gnome Shell, I am not sure if LightDM is the display manager or is GDM?

Can you get to a Grub menu. You may be able to select an earlier kernel that might work. You should be able to select Recovery Mode from there as well. Recovery mode tries to load a log-in screen and desktop without loading a proprietary driver.

I found this statement interesting

> Today's X rarely requires manual configuration. X now automatically configures itself with reasonable defaults.

[https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

It explains why there is not an xorg.conf on my 12.10.

> Most systems don't ship with an X config file any more, but sometimes you need one. Here's a basic skeleton:

> Files ending in *.conf in the /usr/lib/X11/xorg.conf.d/ directory (_NOTE: will be changed to /usr/share/X11/xorg.conf.d for 10.10_) are automatically loaded by X at start prior to reading the xorg.conf. These files can each contain one or more Sections in the same format used by xorg.conf.

Where did you put the xorg.conf? In /usr/share/X11/xorg.conf.d/ ?

---

### Post by Destructo47 on 2012-11-14
```

```LightDM is definitely the [COLOR="Red"]default [/COLOR]DM for Gnome Shell, since I've had to restart it multiple times from console to "unfreeze" the GUI. GDM used to be the default display manager before Oneiric, I believe.

As for X, it's definitely still there. My earlier rescue attempts involved modifying /etc/X11/xorg.conf (which worked before the problem occurred). I needed to use it because X doesn't like my dual-head setup for some reason. Modifying it and trying to reboot does nothing. I had to manually specify the nouveau driver, because the nVidia proprietary drivers available were borked, and it seems nVidia isn't going to fix them. The Vesa driver was also just too slow to work with. Would it help to know I installed packages for nouveau 3D support?

Lastly, I've tried booting into recovery mode, but I can't seem to find a key that brings me to the GRUB menu. I'll keep trying.

I apologize for being impatient, but look at how many unanswered threads I have started, and you'll understand my frustration.

[COLOR="red"]EDIT (11/15/12 @ 23:35)[/COLOR]
I got into the grub menu by holding Shift during boot. Booted into 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)'
Choosing "network" results in a dead end, because it won't let me configure my network connection for some reason or another. "failsafeX" runs fsck, which begins but then stops at ```
/dev/sda3: clean, 130854/17121280 files, 32484995/68469760 blocks
```, so that's another dead end. I reinstalled lightdm, but opted to use gdm instead to see if that changed anything. Now I'm at the same issue, but instead of a blank screen I get the blinking cursor of doom. The X log shows no errors, but one error I do get is "Server is already active for display 0", which I'm guessing means that X doesn't load xorg.conf until the config files from other directories have been loaded, causing some sort of conflict.

It seems I can only use the recovery console via manual commands, since all of the working options induce fsck, which freezes every time. I have to manually mount everything, but I don't know what I should do after that. I'll try renaming/deleting xorg.conf.

---

