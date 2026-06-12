---
title: "Oneiric 11.10: X11 monitor flickering and then gray screen"
date: 2011-10-14
forum: Desktop Environments
---

### Post by mfpompadour on 2011-10-14
I just upgraded my desktop computer to Oneiric 11.10.

The login screen looks just fine.
However, when I log in, X windows starts flickering. After a few minutes, I have a grey screen, and cannot do anything.

Edit: If I log on using Ubuntu 2D, I see a gray screen with mouse as my session is brought up, then I see the standard desktop. There is no flickering, but I get a gray screen and no functionality (no mouse, etc.) after a few minutes.

Edit 2: The screen is completely gray. One color. Not dimmed. Gray.

Edit 3: If I sit on the log in screen, I don't get a locked up machine.

How do I resolve this issue?

---

### Post by therieb on 2011-10-15
I have a similar problem with and Oneiric upgrade to an Asus netbook.  Screen continually goes dim but only in battery mode. I can fix the brightness with the f5 key, but it goes grey again after a minute or so.

---

### Post by therieb on 2011-10-15
Following the advice from [http://ubuntuforums.org/showthread.php?t=1832942&highlight=oneiric+seeker+dpms](http://ubuntuforums.org/showthread.php?t=1832942&highlight=oneiric+seeker+dpms) to add 



Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection

to /etc/xorg.conf 

seems to have fixed the problem on the Asus 1005.  Hope this is is helpful to others

---

### Post by mfpompadour on 2011-10-16
No, I think you have a different problem then me.

The screen is COMPLETELY gray. Not dimmed. GRAY.

---

### Post by bbarwick on 2011-10-18
I'm having the same problem after I upgraded to 11.10. I have a Dell M4600 laptop. If I close my screen and re-open it brings me to the unlock screen. The flickering happens only when the screen seems to rest. Any help would be greatly appreciated. If I figure anything out I will post

-B

---

### Post by cparata on 2011-10-19
I have had the same problem after I upgraded to 11.10 but only once. The screen was completely black and sometimes it appeared and disappeared. I was obliged to reboot. I have an Acer Aspire One D250 laptop. I'm using Unity 2D interface. I'm waiting for another event like that and then I'll post on Ubuntu bug list.

---

### Post by system11 on 2011-10-19
One of our users just 'upgraded' to 11.10 by accident, and the machine (a Thinkpad T420) now has a stretched, offset to the right and flickering display.  It hasn't gone totally grey, it just keeps flickering almost like a failed panel.

---

