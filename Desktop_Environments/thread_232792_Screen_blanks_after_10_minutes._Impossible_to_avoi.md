---
title: "Screen blanks after 10 minutes. Impossible to avoid it"
date: 2006-08-09
forum: Desktop Environments
---

### Post by hexion on 2006-08-09
After searching the net, no solution to my problem.
Just another thread with people complaining with the same, but without answers.

I've decided to open a new thread for if someone read this and knows how to solve the problem.:


THE PROBLEM:
The screen turns black (doesn't turns off, just black screen) after 10 minutes of inactivity. i.e, watching mplayer.

MY SYSTEM:
Ubuntu 6.06 up-to-date, Gnome 2.14.3, XGL+Compiz

WHAT I'VE ALREADY TRIED:

1) Deactivating gnome-power-manager with session manager.
2) Changed options at "Power Manager" and "Screensavers"
3) Changed options with gconf-editor (apps/gnome-power-manager)
4) Removing DPMS line from xorg.conf
5) Added lines to xorg.conf like [Option "BlankTime" "0"] and so.
6) Added option -s 9999 at Xgl script (startxgl.sh)
7) Played with command xset  ([link]("http://www.shallowsky.com/linux/x-screen-blanking.html"))


This bug? is very annoying.
Any ideas?

Thanks in advance.


**EDITED: Problem solved**

To solve this problem (at least worked for me), add this section to /etc/X11/xorg.conf

> Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

---

### Post by ajgreeny on 2006-08-09
Do you know if this happens just with your current monitor or with others as well?  Could it be the monitor at fault, or some wierd setting in that, and perhaps another monitor would be OK?  Just a thought.

---

### Post by hexion on 2006-08-09
I don't think it's my monitor's fault at all..

I never had any problem with it. In fact, many other people has this problem (and only with dapper after upgrading)

I think its a problem with gnome-power-manager, or with the kernel.

Thanks for your answer

---

### Post by tseliot on 2006-08-09
> **hexion said:**
> 2) Changed options at "Power Manager" and "Screensavers"
Did you disable "Activate screensaver when session is idle" in your screensaver preferences?

---

### Post by hexion on 2006-08-09
> **tseliot said:**
> Did you disable "Activate screensaver when session is idle" in your screensaver preferences?

Yes, I did... I played with the whole set of options in fact ;)

---

### Post by hexion on 2006-08-10
Finally someone found the solution (at least for my and his case)

Add this to xorg.conf

> Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

I hope this helps someone if he had this problem too.
Bye

---

### Post by tekDragon on 2006-09-20
This fix appears to have worked for me.

Greatly appreciated.

---

