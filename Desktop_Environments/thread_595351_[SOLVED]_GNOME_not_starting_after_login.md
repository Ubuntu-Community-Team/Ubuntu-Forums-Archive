---
title: "[SOLVED] GNOME not starting after login"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Itried on 2007-10-28
Hi
for  some reason GNOME is not starting after login screen, I get to a pale brown display with no icon, bars etc. If I restart (ctrl alt bckspace) and login with failsafe GNOME sometimes it starts OK, Sometmes not. If I go to terminal (Ctl_Alt_f1), login, then Ctrl-alt F7 and repeat this a few times, GNOME will eventually start properly,
(G'byte GA-P35-DS3 board and G'force 8400 display).

Using Gutsy final release, fresh install, it was all working ok for some days.I think this behaviour began after I first suspended the system.

---

### Post by TeaSwigger on 2007-10-28
> **Itried said:**
> Hi
for  some reason GNOME is not starting after login screen, I get to a pale brown display with no icon, bars etc. If I restart (ctrl alt bckspace) and login with failsafe GNOME sometimes it starts OK, Sometmes not. If I go to terminal (Ctl_Alt_f1), login, then Ctrl-alt F7 and repeat this a few times, GNOME will eventually start properly,
(G'byte GA-P35-DS3 board and G'force 8400 display).

Using Gutsy final release, fresh install, it was all working ok for some days.

Hm. Have you tried creating a new user account (also in sudo "group") to see if that will allow you to log in normally? If it does, there's something amiss in your other user profile and not system wide. Anyway it'd narrow things down.

---

### Post by Itried on 2007-10-29
ta TeaSwigger for the suggestion

created a new Sudoer, now I cant get in at all. Just the login screen, login and just that pale brown display and also no login sound (in WinXP now)

I have posted a edit in my thread about this, but I think this behaviour began after I first suspended the system

---

### Post by Itried on 2007-10-29
I figured from searching other posts, if I wait a while (20 mins!), gnome finally starts right up after login.

---

### Post by TeaSwigger on 2007-10-29
Geez. Well, that's one thing down. What about booting in "recovery mode"? Not that I know how to use it yet. That is a potentially crucial point, the suspend. I'm afraid this is over my head then. I'll poke around for any leads but I hope someone more knowledgeable chimes in meantime.

---

### Post by Itried on 2007-10-29
I can suspend and resume ok once finally booted right in, but only once or twice and the Gutsy will not sudpend at all
Starting gnome fully and immediately however is my immediate concern (sound comes latr)

---

### Post by Itried on 2007-10-29
I followed up this thread [http://ubuntuforums.org/showthread.php?t=582787]("http://ubuntuforums.org/showthread.php?t=582787")

Same problem as me, I still cant find a fix

---

### Post by cikic on 2008-01-23
I have the same problem, only login in gnome failsave mode works.

I tried disabling "Enable accessable login" but this have not solved the problem. Is there anyone who can help he out?

Thanks
Christian

---

