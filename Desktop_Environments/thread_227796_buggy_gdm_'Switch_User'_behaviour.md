---
title: "buggy gdm 'Switch User' behaviour"
date: 2006-08-02
forum: Desktop Environments
---

### Post by KahunaBuntu on 2006-08-02
Hi all,


Firstly, may I declare how impressed I am with 6.06 in general - so impressed in fact that I have blown away my XP partition and just run ubuntu now.


However, there seem to be issues with gdm when attempting to switch users.

When I first installed Dapper, user switching worked like a dream - gdm would start another login splash screen and I could happily run multiple users in parallel.  This behaviour was stable for ~20 boots.

However, gdm user switching is now broken with a variety of messages, after *NO CHANGE* to xorg.conf or gdm.conf files (I verified this with md5sum from original md5s of the files when user switching was working).

Now when clicking on the Shutdown>Switch User button, either one of three things occurs:

1) gdmflexiserver throws a window with caption "Cannot start new display", and a sub-caption which is something like "xorg.conf may be badly configured." (sorry - can't remember the original message and it isn't doing this at the moment)

2) screen locks (like it does after inactivity period), when disturbed get a password prompt for the currently logged on user.  The 'Switch User' button is present and clicking it brings up a list of computer users.  However, selecting any of them does *nothing*.  No prompt, absolutely nothing.

3) Neither of the above occur, it is as if you haven't clicked the button, with the exception of entries in /var/log/syslog like this:

Aug  2 12:30:56 x505 gdm[4098]: gdm_child_action: Aborting display :-1
Aug  2 12:44:28 x505 gdm[4098]: gdm_child_action: Aborting display :-1
Aug  2 12:55:12 x505 gdm[4098]: gdm_child_action: Aborting display :-1


The hardware is a Sony vaio VGN-X505VP with Intel 82852/855GM graphics chipset.


Any X or gdm devs out there got any ideas as to what this might be, or can suggest any debug output that I can retrieve to try and understand what's going on?

Any assistance gratefully appreciated.


KB

---

### Post by KahunaBuntu on 2006-08-03
missing error message:

Cannot start new Display

The X server failed.  Perhaps it is not configured well.


Any ideas people?

---

### Post by Nokia on 2006-08-11
I've seen this on several desktop and laptop computers, all of them fully upgraded, so I presume they're already working on this issue. I hope those who can do something about it will give us an answer asap, either here or via apt-get :)

---

### Post by Nokia on 2006-08-13
Yesterday updates seemed to fix this issue. I can confirm everything is working fine on nvidia-based systems. I suppose it'll be fine on Ati as well, but I can't confirm just yet :)

---

