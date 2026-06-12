---
title: "Dapper logs out automatically w/o warning"
date: 2006-09-21
forum: Desktop Environments
---

### Post by schaefscha on 2006-09-21
So I had the problem that my Xorg didn't work, so I had to update the whole ubuntu two days ago. Now it's running Dapper, but since then it is constantly logging out without me wanting it to do it (like every 15 minutes, or sooner when I'm using the Terminal or Synaptic). It's really bothering me, since sometimes I'm in the middle of writting an e-mail and it just comes up a black screen without notice and the login page shows up, no chance to save and everything is lost.

Anyone has a clue?

PS- at least Xorg is now working!

---

### Post by rjm1982 on 2006-09-21
I would imagine you are accidentally hitting ctrl-backspace maybe?

I kept doing the same thing...

Maybe not, but it appears its doing it as you type...so that might be it...im on a laptop so the buttons are super touchy so i just disabled it.

---

### Post by nazish on 2006-09-21
do u use XGL and compiz if so by pressing the combination> SHIFT+BACKSPACE restarts XGL server.

---

### Post by schaefscha on 2006-09-22
Thnx for the hints, but that doesn't seem to be the problem, since my XGL is off.
And the automatic log out happened also when I was just using the mouse (like when scrolling down the software list in Synaptic).

---

### Post by DarkStarDeity on 2006-09-22
I'm getting the same thing happening, although on my machine it is happening when the screensaver is on. I'll come back after leaving my machine on  overnight to find it has logged me out (possibly restarted the machine from the system log, but I may be reading that wrong) at some stage during the night. It always seems to happen when I leave Firefox open, so this time I shut Firefox before leaving the computer and my session stayed up, but it logged me out again as soon as started Firefox.

This only started after upgrading the kernel to 2.6.15-27-386 the other day. 

Anyone else seeing (semi-)random logouts since the kernel upgrade?

---

### Post by de4th on 2006-09-23
I don't have auto logouts but my display goes on sleep mode after some time.
I configured power management to "never" but it still goes...
Same kernel after update here.


PS. Kernel 2.6.15-27-386 is great for ram usage!

---

### Post by de4th on 2006-09-24
All fixed! When you update your kernel restart your pc.
Do your configuration for your screensaver & power management and restart again. It worked for me. :cool:

---

### Post by lawchilly on 2006-10-30
I am having this problem also. But the display goes half-black half garbled for a second then I get back to the logon screen. Its a brand new install and I keep on thinking I have fixed it and it breaks again.

Also seems to happen when using firefox / doing things with sound.

definitely not any keyboard combination issue as it has happened when I have been half a room away from my pc.

I will look at the power management options but what exactly should I be looking at??](*,)

---

### Post by DarkStarDeity on 2006-10-30
I found that unchecking "Activate screensaver when session is idle" (and rebooting) seems to have fixed this problem for me. I can still manually lock my screen (which brings up the screensaver), so it's not the screensaver itself, but it seems that whatever is polling the system for user activity is causing applications (including the gnome desktop itself) to crash.

---

