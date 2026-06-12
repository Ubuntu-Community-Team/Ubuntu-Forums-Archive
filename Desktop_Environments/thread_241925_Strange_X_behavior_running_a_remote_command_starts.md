---
title: "Strange X behavior: running a remote command starts a local process?"
date: 2006-08-23
forum: Desktop Environments
---

### Post by Kensey on 2006-08-23
OK, so I just resurrected my old Debian box (crowley) from cold storage.  After getting it booted, fscked, and updated (sarge is Debian-stable now?  My, how time flies...), I've been playing with it.

If I have ssh X forwarding on so I can run apps from crowley and display on my Ubuntu laptop (azazel), I've noticed an odd behavior: if I run apps on crowley that are also installed on azazel, a local copy starts up on azazel instead of a remote copy on crowley displaying to here.  This is how it goes:

[list]
[*]crowley:~/apps/firefox-0.8$ ./firefox &
[indent]starts a copy from crowley displaying to azazel[/indent]
[*]crowley:/usr/bin$ ./firefox &
[indent]starts a copy from azazel[/indent]
[*]crowley:~$ firefox &
[indent]starts a copy from azazel[/indent]
[/list]

Anything installed on crowley but not on azazel starts a process on crowley that displays on azazel, which is what I expect to happen in all cases and used to be how X forwarding always worked when I was going from one Debian box to another.  How do I control this new behavior?  It's unusual (to me, anyway) to say the least.

---

### Post by Jussi Kukkonen on 2006-08-23
Are you sure it's running on the local machine, and not just using the profile from the local machine?

---

### Post by Kensey on 2006-08-23
Pretty sure -- if Firefox is running locally it shows a normal titlebar with my current bookmarks and the app shows the version installed on azazel (1.5.0.6), and if it's running on crowley the titlebar says "(on crowley)" at the end, the version is the version on crowley (1.0.4), and it has my old bookmarks from crowley.

Additional oddness: if I shut down all Firefoxes running on azazel, then run "firefox &" in a session to crowley, I get crowley's firefox.  So whether I get a local or remote instance seems to depend on whether the app is already running locally.

---

