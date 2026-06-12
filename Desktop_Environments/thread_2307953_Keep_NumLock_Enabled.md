---
title: "Keep NumLock Enabled"
date: 2015-12-29
forum: Desktop Environments
---

### Post by snakyjake on 2015-12-29
How do I keep the keyboard numlock (number lock) enabled when the screen saver is activated or the screen is locked?

There shouldn't be a valid reason why Xubuntu is toggling my numlock.  Seems like a bug to me.
I don't want to install anything extra.

Xubuntu 15.10

---

### Post by thorsten-munsch on 2016-01-22
I can confirm that. At work I have a Debian 8.1 with Xfce 4.10 and the Numlock stays always on. 

I have two private machines which are affected on the bug. All Xubuntu 14.04 LTS with Xfce 4.10..one selfmade desktop pc, one hp elitebook.

---

### Post by Dennis N on 2016-01-22
On Xubuntu 15.10, I find that if **Settings > Keyboard > Restore Numlock State on Startup** is checked, and Numlock is ON when you shut down, it will be ON after restart and log in. My screensaver is not affecting the numlock state but I do not lock the screen.

---

### Post by speartip on 2016-01-23
> **Dennis N said:**
> On Xubuntu 15.10, I find that if **Settings > Keyboard > Restore Numlock State on Startup** is checked, and Numlock is ON when you shut down, it will be ON after restart and log in. My screensaver is not affecting the numlock state but I do not lock the screen.

That's true, but not after locking or suspending the computer.

---

### Post by Nuno_Abreu on 2016-01-23
Have you tried to use **numlockx**?

Then you can add this command on rc.local or in a startup script (it might be optional):
```
numlockx on
```

---

### Post by speartip on 2016-01-24
> **Nuno_Abreu said:**
> Have you tried to use **numlockx**?

Then you can add this command on rc.local or in a startup script (it might be optional):


Again, the problem isn't numlock being enabled on startup or login. It's when the screensaver is activated, locked or resuming from suspend.

@snakyjake... Is this problem, that the number pad is disabled or just that the numlock light goes out? In my case the pad remains active but the light goes out as if it's disabled.

---

### Post by ggallozz on 2016-07-02
same problem here.

kernel name is: Linux
kernel-release is: 3.16.0-72-generic
kernel version is: #93~14.04.1-Ubuntu SMP Mon May 16 21:28:40 UTC 2016
machine hardware is: i686
processor type is: i686
h/w platform is: i686
operating system is: GNU/Linux
desktop env. is: xubuntu - XDG_CURRENT_DESKTOP=XFCE
*** OS specs ***
Distributor ID: trusty
Description: Ubuntu
Release: Ubuntu 14.04.4 LTS
Codename: 14.04

---

### Post by pqwoerituytrueiwoq on 2016-07-04
using xubuntu 14.04 and 16.04 i have no issue with this
Since OP wants to not use extra software, i did look for a alt way and dug this up
i managed to find this folder
[FONT=courier new]/sys/class/leds/input3::numlock[/FONT]
Turn LED on
[FONT=courier new]echo 1 | sudo tee /sys/class/leds/input3::numlock/brightness[/FONT]
Turn LED off
[FONT=courier new]echo 0 | sudo tee /sys/class/leds/input3::numlock/brightness[/FONT]
this has no effect on the numlock state only the LED

if it really is turning off randomly just use a cronjob can call [FONT=courier new]numlockx on[/FONT] every minute, very dirty workaround
edit: you mean you don't have numlock at the login screen right?
look at this file: [FONT=courier new]/etc/lightdm/lightdm.conf[/FONT]
you will either need to use [FONT=Courier New]greeter-setup-script[/FONT] or [FONT=Courier New]display-setup-script[/FONT] not sure which, may work with either
```
me@A54C-NB91:/sys/class/leds/input3::numlock$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
greeter-setup-script=/usr/bin/numlockx on
#display-setup-script =/usr/bin/numlockx on
```

i use xscreensaver, not lite-locker, if recall lightlocker uses the login screen for the password prompt, this is not the user session therefore your user numlock setting does not mean anything

---

