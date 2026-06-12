---
title: "XFCE : text input problem as user"
date: 2007-04-30
forum: Desktop Environments
---

### Post by xSauronx on 2007-04-30
Ive been dealing with this problem on and off for a few weeks, so Ill start with the exact problem, and what Ive tried to do to solve it, or at least figure out *why* it is happening.


My system:

XFCE 4.4 on [Debian Etch (Stable)/Xubuntu 7.04] on my Inspiron 1000
The Problem:

Text input in XFCE is bonkers. It randomly refuses my input. Letters, numbers, spaces, etc, all randomly *do not* show up. It makes typing a bitch, as you can imagine. I did *not* have this problem in Xubuntu 6.10

The Beginning:

I had used Xubuntu 6.10 for a few months, and wanted to switch to straight Debian to learn more about Linux and how it works. I used Xubuntu because i have an Inspiron Laptop with a 2200mhz Celeron cpu and under a gig of ram. With Xubuntu I never encountered the current problem.

I switched to Debian Etch a few weeks before the stable release, installed a base system (wanting as light an install as possible) and then XFCE on top of it, among other things. I soon began to have this strange input problem.

Finding a Solution:

I started by googling, and got nothing.
I posted looking for help in AnandTech OS Forums, and got a few suggestions.
Ive posted in the debian user forums, and had some suggestions.
Ive posted in the XFCE forums which seem to be near-dead.
Ive asked in #debian and #debian-xfce on freenode.
Ive googled more.

What Ive Tried:

Ive checked logs and dmesg for any kb or input-related errors and found nothing.
Ive booted into single-user mode, and done #~:startx
-there was no input problem in this instance, _ever_.

Ive booted into regular mode, started a failsafe terminal as a user.
-there was no problem in the failsafe terminal

Ive booted regularly, logged in as a user, killed gdm and run xsx@actium~:startx
-this did not help.

Ive deleted ./config/xfce4-sessions/xfce4-sessions.rc
--this seemed to fix it, then it happened again and now deleting it doesnt do anything.

I installed IceWM and have *ZERO* problems with input
-i dont like Ice and want to use XFCE

Ive tried eLive with E17 and did not have the problem(thought perhaps it was an Etch glitch, since Xubuntu 6.10 worked fine)

I installed QT apps on the suspicion from someone it was a GTK problem
-the QT apps have the same problem under XFCE as GTK apps

Ive toyed with various xorg.conf settings from other inspiron users for the hell of it. i figure if it works in single user mode, its not X, but it was worth a shot.

I also changed the keymapping in the XFCE4 keyboard settings; still nada.

I dont know where to turn to fix this, or at least find out whats causing it. Clearly, its fixable, since logging into single-user mode and running it as root has no issues, and IceWM/E17 as a user has no issues.

-emailed XFCE mailing list: no response so far :/

Anyone have any ideas on what I can try? I really like XFCE


#### Cliffs

XFCE text input farked
Works in single-user mode as root
Works in IceWM/E17
Ive tried alot of stuff
It still doesnt work and i want to set something on fire.

--dave

---

### Post by dolphin_oracle on 2007-04-30
I had a similar problem after an update to Xubuntu edgy.  I never figured it out and reinstalled to fix the problem.  I fear it returning, so am not updating the system at the moment.

My problem was only in Abiword.  It worked fine in Openoffice.  I found that my text was there, it just wasn't displaying correctly.  A quick font change to Times New Roman made everything show up again, but most other fonts didn't work.

Since my reinstall everything has been fine, but like I said, I haven't run any updates yet.

Good luck.

---

### Post by xSauronx on 2007-05-01
well it worked fine when i ran edgy, no good under debian etch, etc

it *only*  is problematic when logged in as a user in XFCE.

its *really* bugging me, maybe i should mail the devs or someoneto see if i can find any ideas. wtf could be so different between the root and user account that could cause the text entry to fark up? :(

thanks though

---

### Post by xSauronx on 2007-05-01
no other ideas?

---

