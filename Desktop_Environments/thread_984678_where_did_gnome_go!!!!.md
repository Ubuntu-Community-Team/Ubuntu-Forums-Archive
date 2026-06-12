---
title: "where did gnome go?!?!?!?!"
date: 2008-11-16
forum: Desktop Environments
---

### Post by Maximusmaximus on 2008-11-16
i booted up my computer today and it did its usual start up sequence and after the Ubuntu loadning screen it sent me to a blank screen with only this written:


starting up...
loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-vvid/83cdc2b3-fe2d-4320-9754-b63b2087cc0f) = sda(8,5)
kinit: no resume image, doing normal boot...

ubuntu 8.04.1 kev-desktop tty1

kev-desktop login:



does anywhere know where gnome went? if it helps i had a compiz-fusion desktop run by an Nvidia 7800 series with the latest drivers all working perfectly. (i am a ubuntu n00b for the record)

---

### Post by Marcus Derekus on 2008-11-16
After your system boots up try pressing  **ctrl + alt + F7**

please post results

---

### Post by matmarroba on 2008-11-19
Obviously Ctrl+Alt+F7 does nothing at this point. I have the same problem.
This conversation should be moved to:
[http://ubuntuforums.org/showthread.php?t=984651](http://ubuntuforums.org/showthread.php?t=984651)
/M

---

### Post by win4thebin on 2008-11-19
Try logging in like you normally would so [I]etc-desktop: etc
Password: something[/I]. gnome might be there afterwards otherwise post another message.

---

### Post by matmarroba on 2008-11-19
I meant after logging in. Ctrl+Alt+ (F1..F6) changes between the TTY's, but F7 does nothing at all.

No amount of rebooting or trying "xfix" or repairing broken packages works, I'm afraid. Also, apt-get doesn't work. It says

gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new

And when I try to start emacs, it says

emacs: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled

And I'm trying to start emacs in tty1 here! Why does it think it needs some GTK?

And I can't re-install glib/gtk or whatever because apt-get/dpkg doesn't work! Do I really have to reinstall my system? It sure seems so :(

I really want my desktop back! This computer I'm using right now is... not good.

---

### Post by fornix on 2008-11-19
Login ur console and try this
```
$ startx
```
If that doesn't take you to gui, try this
```
$ sudo /etc/init.d/gdm start
```

---

### Post by snova on 2008-11-19
The error message in the first post happens (or used to happen) to me also, so I think it is not relevant.

Emacs... it depends on which version you installed. I think the default is the GUI version (the term one is emacs-nox, I believe).

Try the 'startx' command as previously suggested and look for error messages. This will manually start the X server, which will probably fail, which will also hopefully tell us what's wrong.

The apt-get error doesn't look good. It also seems familiar...

---

### Post by matmarroba on 2008-11-20
startx shows a very grey GUI with a mouse pointer, but nothing else. Ctrl+C in X does nothing, but it disappears when I Ctrl+Alt away and back. The only way to get it away is Ctrl+Alt+F2 then Ctrl+Alt+F1 back to the tty and Ctrl+C to exit.
I've pretty much given up and soon I'm gonna reinstall ubuntu.

gdm gives a simple message: [Fail]

---

### Post by hakvoort on 2008-11-20
try to boot in the recovery mode and run 'try to fix x server',maybe that will solve your problems

---

### Post by snova on 2008-11-20
Recovery mode is worth a shot.

When you boot up, press Esc a few times until you get a menu. Select the first entry you see with "recovery mode" and press enter.

This will boot up a minimal system and present another menu. Select "Fix X" and press enter again, and when it's done, continue booting as normal.

It might not work, but it's worth a try.

---

