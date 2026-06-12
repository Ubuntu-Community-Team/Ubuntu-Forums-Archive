---
title: "flipped screen"
date: 2010-04-05
forum: Desktop Environments
---

### Post by andreselsuave on 2010-04-05
Hello guys!

I have a problem: 
I have been using kde for a while and now when I try to start gnome with any user, the screen is rotated 180º and also appears to be flipped horizontally.

How can I fix this? 

I have tried reinstalling ubuntu-desktop and gdm, but with no success.

Thanks a lot.
andreselsuave

---

### Post by kblft on 2010-04-05
After you log into gnome - have you tried :
System -> Preferences -> Display 
then check if you have rotation set in any way

---

### Post by SaintDanBert on 2010-04-05
(chuckle) Are you sure that you didn't step through the glass and are looking at things from the back side?

I move between KDE and GNOME and frequently have this happen to me.
Sorry, I don't know why it happens. I suspect that I'm using some application that is leaving config details in one of the $HOME dot-folders and then things get scrambled during the switch.
I'm going through my X11 session files -- whatever starts at login --
checking for the miscreant. I wish I had more to offer than a bad joke.

If someone finds the cause or a way to stop this, I'd love to find out.

~~~ 0;-Dan

---

### Post by andreselsuave on 2010-04-05
I can't, because the buttons work as if it was not rotated, so I don't know where to click... can I start that from the terminal?

but I don't think that's the problem since all the users have the same problem

edit:
I managed to get to the screen manager, but it is set to Normal. Trying to rotate it doesn't help at all.

---

### Post by andreselsuave on 2010-04-05
Running Failsafe GNOME does the trick, but I would like to solve it in a better way ... :/

thanks :)

---

### Post by nietofarias on 2011-01-10
I have the same problem
Do you have already a solution for it?
[http://img30.imageshack.us/i/pantallazoyk.png/](http://img30.imageshack.us/i/pantallazoyk.png/)

[IMG]http://img30.imageshack.us/i/pantallazoyk.png/[/IMG]

---

### Post by nietofarias on 2011-01-10
I've found that the intel driver is causing the problem:
Section "Device"
    Identifier    "Default Device"
    Driver    "intel"
    BusID        "PCI:0:2:0"
EndSection

The failsafe mode, with the other driver works fine:
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

But the /var/log/Xorg.*.log doesn't show any EE lines
This was working fine until the latest big update I did with 100mb of updates. Cannot tell which package specifically created this problem

---

