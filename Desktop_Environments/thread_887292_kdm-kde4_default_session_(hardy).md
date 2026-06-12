---
title: "kdm-kde4 default session (hardy)"
date: 2008-08-12
forum: Desktop Environments
---

### Post by awry on 2008-08-12
I have both kde 3.5.9 and 4.1.0 installed on my hardy system.  I almost always use kde4 now, but haven't entirely let go of kde3 yet.  I'm using kdm-kde4 as my login manager, and it *always* loads kde3 by default.  

My understanding is that kdm is supposed to remember your last session type, and use that as the default.  Yet despite always using kde4, kdm-kde4 insists on loading kde3.  

I've tried setting Type=Default in /usr/lib/kde4/share/kde4/apps/kdm/sessions/kde.desktop per the kde docs, but that does not solve the problem.  None of the other *.desktop entries in the sessions path have Type=Default set.

Anyone have any clues?  Is it just me or do others have this issue?

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by jimbudler on 2008-10-07
Contents of ~/.dmrc for me

[Desktop]
Session=kde4
Language=en_US.UTF-8

It was Session=Fvwm until I logged into a console window, edited it and and restarted kdm.

Jim

---

