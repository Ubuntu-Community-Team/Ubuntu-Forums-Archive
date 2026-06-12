---
title: "Ubuntu 20.04.2 - Suddenly can't suspend, Ryzen desktop"
date: 2021-05-03
forum: Desktop Environments
---

### Post by sorceror171 on 2021-05-03
I've been suspending my desktop when not in use since I got it, in early 2020. In the last couple days it doesn't suspend. It just locks the screen, but the computer never goes to sleep.

I can't find anything that seems relevant in dmesg or the various logs in /var/log. What's the procedure to debug this stuff?

Xubuntu 20.04.2, Asus Crosshair VIII Hero motherboard, Ryzen 9 3950X CPU. No hardware changes or new devices plugged in recently.

---

### Post by sorceror171 on 2021-05-03
One minor note - I just realized one other possibly-relevant change in behavior. When I plug in a USB flash drive, all of a sudden it's asking for my password to mount it. Never used to do that before.

---

### Post by TheFu on 2021-05-03
```
sudo pm-suspend
```
Does that work? if so, it is only a GUI thing, not deeper.

If you create a new userid, does suspend work from that account? If so, it is a personal settings problem that needs to be cleaned up. This is harder than it sounds.

---

### Post by sorceror171 on 2021-05-04
Unfortunately, ```
sudo pm-suspend
``` gets: ```
sudo: pm-suspend: command not found
```

Did a bit of googling, and tried: ```
systemctl suspend
```

I'm afraid I got the same behavior as when using the system menu: the screen locked, but the computer did not sleep/suspend.

I created a test user, and... same behavior. Suspend only locks screen, doesn't put the computer to sleep. In fact, for a bit there the 'suspend' button disappeared from the Xubuntu 'power' menu. It's back now, but still doesn't work.

(While creating the test user, I saw that the permission "Access external storage devices automatically" is checked for me. That hasn't change, but the good news is I can stick in flash media and have it automatically mount.)

---

### Post by ajgreeny on 2021-05-04
I also get the same "command not found" when running ***sudo pm-suspend*** on my Xubuntu 20.04 but I think that is because I do not have the pm-utils package installed.

Using Xubuntu I have a keyboard shortcut linked to the Pause/Break key which uses command ```
xfce4-session-logout --suspend
``` which works fine and as user, with no need for sudo, so that is what I use most for an instant suspend.

However, having just now installed the **pm-utils** package on my system, the **sudo pm-suspend** command that did not work before, now works as expected.

Having just noticed that you are also running Xubuntu, why not try adding the command I show to your keyboard shortcuts as I have; it's something I ise on both my laptop and desktop but more on the latter as that, of course, has no lid switch which suspends the laptop as well as the Pause/Break key.

---

### Post by sorceror171 on 2021-05-04
OK, weirdness I don't like. I discovered today that Steam couldn't see my XBox 360 controller all of a sudden, though that's been working well before now. Oddly, jstest *could* see it.

I added myself to the 'input' group, logged out and back in, and now Steam can see the controller.

I'm worried that permissions got messed up on this machine. I did try:

```
xfce4-session-logout --suspend
```

...but same behavior. Screen locks, computer doesn't sleep. I wonder if I'm suddenly missing a relevant permission? And if so... is there a log *somewhere* that'll tell me what it is?

---

### Post by sorceror171 on 2021-05-05
Hmm. Installed **pm-utils**, and **sudo pm-suspend** does in fact put the computer to sleep. I can't figure out *why* permissions have changed, but it's gotta be something along those lines...

---

### Post by ajgreeny on 2021-05-05
> **sorceror171 said:**
> Hmm. Installed **pm-utils**, and **sudo pm-suspend** does in fact put the computer to sleep. I can't figure out *why* permissions have changed, but it's gotta be something along those lines...
Now that you have the ***sudo pm-suspend*** command working, see if my suggestion of the keyboard shortcut for ***xfce4-session-logout --suspend*** also works.

It is so incredibly useful on my desktop machine as it means a single key press at any moment with no password needed suspends the system immediately.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by sorceror171 on 2021-05-05
Unfortunately, while **sudo pm-suspend** does *suspend* things, it's not quite a satisfactory solution, since it doesn't lock the screen. And while **xfce4-session-logout --suspend** and the XFCE "Suspend" GUI button *do* lock the screen... they don't suspend the power. So for now, I've got two half-solutions that don't add up to a whole one.

I suppose the next step is to try to debug using dbus logs or something? Maybe I should ask on the Desktop Environments forum at this point?

---

### Post by mastablasta on 2021-05-06
if it suspends then it's not a hardware issue. did you do any installs or mess with permission files? maybe running any GUI app with sudo command?

---

### Post by sorceror171 on 2021-05-06
I honestly don't know of anything special. The most I did was try to upgrade to the 465 version of the Nvidia proprietary driver. That failed - Steam wouldn't load. So I dropped back to 460, which I'd been using. That's literally the only thing I know of, though I did do a **sudo apt-get update;sudo apt-get dist-upgrade** along the way.

---

### Post by sorceror171 on 2021-05-08
I've been suspending my desktop (using the XFCE menu "Suspend" button) when not in use. It's been working fine since I got this computer, in early 2020. About a week ago, it suddenly stopped suspending. It only locks the screen; the computer never actually goes to sleep.

I can't find anything that seems relevant in dmesg or the various logs in /var/log. Following advice from this thread ([https://ubuntuforums.org/showthread.php?t=2461572](https://ubuntuforums.org/showthread.php?t=2461572)), I installed the **pm-utils** package, and using the command **sudo pm-suspend**, the computer will go to sleep. But then it doesn't lock the screen.

At the same time, automatically mounting USB media stopped working. It asks for my password now, every time. I've checked in "Users and Groups", and I have the "Access external storage devices automatically" privilege checked. But every time, I have to authenticate to mount or eject.

Additionally, Steam suddenly couldn't see my game controller. Using "Users and Groups", I added myself to the 'input' group, and that seems to have gotten *that* working, at least.

Xubuntu 20.04.2, Asus Crosshair VIII Hero motherboard, Ryzen 9 3950X CPU. No hardware changes or new devices plugged in recently. At around the time things stopped working, I attempted to update my Nvidia proprietary driver to the 465 version (using the standard Ubuntu PPA), but that broke accelerated graphics. I dropped back to 460, and graphics were restored. I don't know how that would affect suspend and automount, though.

What's the procedure for debugging something like this? I really shouldn't have to reinstall to get this stuff working again...

---

### Post by ajgreeny on 2021-05-08
Threads merged.

Please **do not repost exactly the same problem as a duplicate thread** simply because you have so far not managed to acquire a solution to your problem.
Doing so will not increase the likelihood of getting what you want and will probably be very confusing for all of us, including you.

---

